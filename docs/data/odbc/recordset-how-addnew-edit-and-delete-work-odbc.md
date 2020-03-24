---
title: 'Sada záznamů: Funkce operací AddNew, Edit a Delete (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
ms.openlocfilehash: 8799ac36c443898f1e32b539f017e682bbf3e033
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212901"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Sada záznamů: Funkce operací AddNew, Edit a Delete (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak `AddNew`, `Edit`a `Delete` členské funkce třídy `CRecordset` fungují. Probíraná témata zahrnují:

- [Způsob přidávání záznamů funguje](#_core_adding_a_record)

- [Viditelnost přidaných záznamů](#_core_visibility_of_added_records)

- [Jak fungují úpravy záznamů](#_core_editing_an_existing_record)

- [Jak funguje odstraňování záznamů](#_core_deleting_a_record)

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, přečtěte si téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jako doplněk můžete chtít přečíst [pole záznamu výměna: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), což popisuje odpovídající roli RFX v operacích aktualizace.

##  <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Přidání záznamu

Přidání nového záznamu do sady záznamů zahrnuje volání členské funkce [AddNew](../../mfc/reference/crecordset-class.md#addnew) sady záznamů, nastavení hodnot datových členů pole nového záznamu a volání funkce členu [aktualizace](../../mfc/reference/crecordset-class.md#update) pro zápis záznamu do zdroje dat.

Jako podmínku pro volání `AddNew`nesmí být sada záznamů otevřena jako jen pro čtení. Členské funkce `CanUpdate` a `CanAppend` vám umožňují určit tyto podmínky.

Při volání `AddNew`:

- Záznam ve vyrovnávací paměti pro úpravy je uložen, takže jeho obsah lze obnovit, pokud je operace zrušena.

- Datové členy pole jsou označeny příznakem, takže je možné později zjistit změny v nich. Datové členy pole jsou také označeny jako čisté (beze změny) a nastaveny na hodnotu null.

Po volání `AddNew`představuje upravená vyrovnávací paměť nový prázdný záznam, který je připravený k vyplnění hodnotami. K tomu je třeba ručně nastavit hodnoty jejich přiřazením. Namísto zadání skutečné hodnoty dat pro pole můžete volat `SetFieldNull` k určení hodnoty null.

Chcete-li potvrdit změny, zavoláte `Update`. Když zavoláte `Update` pro nový záznam:

- Pokud ovladač ODBC podporuje funkci `::SQLSetPos` rozhraní ODBC API, knihovna MFC použije funkci k přidání záznamu do zdroje dat. Pomocí `::SQLSetPos`může MFC přidat záznam efektivněji, protože není nutné sestavit a zpracovat příkaz SQL.

- Pokud `::SQLSetPos` nelze použít, knihovna MFC provede následující akce:

   1. Pokud se nezjistí žádné změny, `Update` neprovede žádnou akci a vrátí hodnotu 0.

   1. Pokud dojde ke změnám, `Update` vytvoří příkaz SQL **INSERT** . Sloupce reprezentované všemi datovými členy pole Dirty jsou uvedeny v příkazu **INSERT** . Chcete-li vynutit zahrnutí sloupce, zavolejte členskou funkci [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) :

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` potvrdí nový záznam – příkaz **INSERT** je proveden a záznam je potvrzen do tabulky ve zdroji dat (a sadě záznamů, pokud není to snímek), pokud transakce neprobíhá.

   1. Uložený záznam se obnoví do vyrovnávací paměti pro úpravy. Záznam, který byl aktuální před voláním `AddNew`, je opět aktuální bez ohledu na to, zda byl příkaz **INSERT** úspěšně proveden.

   > [!TIP]
   > Pro úplnou kontrolu nového záznamu Vezměte v úvahu následující přístup: nastavte hodnoty všech polí, která budou mít hodnoty, a pak explicitně nastavte všechna pole, která budou mít hodnotu null, voláním `SetFieldNull` s ukazatelem na pole a parametrem TRUE (výchozí). Chcete-li zajistit, že pole není zapsáno do zdroje dat, zavolejte `SetFieldDirty` s ukazatelem na pole a parametr FALSE a hodnotu pole neupravujte. Chcete-li zjistit, zda je pole může mít hodnotu null, zavolejte `IsFieldNullable`.

   > [!TIP]
   > Pro zjištění, zda datové členy sady záznamů mění hodnotu, používá knihovna MFC hodnotu PSEUDO_NULL vhodnou pro každý datový typ, který lze uložit do sady záznamů. Pokud je nutné explicitně nastavit pole na PSEUDO_NULL hodnotu a pole je již označeno jako null, je nutné také volat `SetFieldNull`, předávání adresy pole v prvním parametru a FALSE ve druhém parametru.

##  <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Viditelnost přidaných záznamů

Kdy je přidaný záznam viditelný do vaší sady záznamů? Přidané záznamy se někdy zobrazují a někdy nejsou viditelné, v závislosti na dvou věcech:

- K čemu je váš ovladač schopný.

- Co může rozhraní využít.

Pokud ovladač ODBC podporuje funkci `::SQLSetPos` rozhraní ODBC API, knihovna MFC použije funkci pro přidání záznamů. Pomocí `::SQLSetPos`jsou přidané záznamy viditelné pro libovolnou aktualizovatelnou sadu záznamů MFC. Bez podpory pro funkci nejsou přidané záznamy viditelné a je třeba volat `Requery` pro jejich zobrazení. Použití `::SQLSetPos` je také efektivnější.

##  <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Úprava existujícího záznamu

Úprava existujícího záznamu v sadě záznamů zahrnuje rolování na záznam, volání [editační](../../mfc/reference/crecordset-class.md#edit) členské funkce sady záznamů, nastavení hodnot datových členů pole nového záznamu a volání funkce členu [aktualizace](../../mfc/reference/crecordset-class.md#update) pro zápis změněného záznamu do zdroje dat.

Pro volání `Edit`musí být sada záznamů aktualizovatelná a na záznamu. Členské funkce `CanUpdate` a `IsDeleted` vám umožňují určit tyto podmínky. Aktuální záznam také nesmí být odstraněn a v sadě záznamů musí být záznamy (`IsBOF` a `IsEOF` vrátí 0).

Při volání `Edit`je uložen záznam ve vyrovnávací paměti pro úpravy (aktuální záznam). Hodnoty uloženého záznamu se později používají k detekci, jestli se některá pole změnila.

Po volání `Edit`, vyrovnávací paměť úprav stále představuje aktuální záznam, ale nyní je připravena přijmout změny v polích datových členů. Chcete-li změnit záznam, ručně nastavte hodnoty všech datových členů pole, které chcete upravit. Namísto zadání skutečné hodnoty dat pro pole můžete volat `SetFieldNull` k určení hodnoty null. Chcete-li potvrdit změny, zavolejte `Update`.

> [!TIP]
> Chcete-li získat z režimu `AddNew` nebo `Edit`, zavolejte `Move` s parametrem *AFX_MOVE_REFRESH*.

Sada záznamů jako podmínku pro volání `Update`nesmí být prázdná a aktuální záznam nesmí být odstraněn. `IsBOF`, `IsEOF`a `IsDeleted` by měly vracet 0.

Když zavoláte `Update` pro Upravovaný záznam:

- Pokud ovladač ODBC podporuje funkci `::SQLSetPos` rozhraní ODBC API, knihovna MFC pomocí funkce aktualizuje záznam ve zdroji dat. Při `::SQLSetPos`ovladač porovnává vaši upravenou vyrovnávací paměť s odpovídajícím záznamem na serveru a aktualizuje záznam na serveru, pokud jsou tyto dva odlišné. Pomocí `::SQLSetPos`může knihovna MFC aktualizovat záznam efektivněji, protože není nutné sestavit a zpracovat příkaz SQL.

   \- nebo-

- Pokud `::SQLSetPos` nelze použít, knihovna MFC provede následující akce:

   1. Pokud se žádné změny nezměnily, `Update` neprovede žádnou akci a vrátí hodnotu 0.

   1. Pokud dojde ke změnám, `Update` vytvoří příkaz SQL **Update** . Sloupce uvedené v příkazu **Update** jsou založeny na polích datových členů, které byly změněny.

   1. `Update` potvrdí změny – spustí příkaz **Update** – a záznam se změní ve zdroji dat, ale není potvrzen, pokud probíhá transakce (viz [transakce: provedení transakce v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) pro informace o tom, jak transakce ovlivňuje aktualizaci). Rozhraní ODBC uchovává kopii záznamu, který se také změní.

   1. Na rozdíl od procesu pro `AddNew`neobnoví proces `Edit` uložený záznam. Upravovaný záznam zůstane na místě jako aktuální záznam.

   > [!CAUTION]
   > Při přípravě na aktualizaci sady záznamů voláním `Update`se ujistěte, že vaše sada záznamů obsahuje všechny sloupce, které tvoří primární klíč tabulky (nebo všechny sloupce libovolného jedinečného indexu v tabulce nebo dostatek sloupců k jedinečné identifikaci řádku). V některých případech může rozhraní použít pouze sloupce vybrané ve vaší sadě záznamů k identifikaci záznamu v tabulce, který chcete aktualizovat. Bez všech potřebných sloupců může být v tabulce Aktualizováno více záznamů. V tomto případě rozhraní vyvolá výjimky při volání `Update`.

   > [!TIP]
   > Pokud zavoláte `AddNew` nebo `Edit` po volání buď dříve, ale před voláním `Update`, upraví se vyrovnávací paměť pro úpravu uloženým záznamem a nahradí se nový nebo Upravovaný záznam. Toto chování dává způsob, jak přerušit `AddNew` nebo `Edit` a začít nové: Pokud zjistíte, že záznam probíhá, je poškozený, jednoduše zavolejte `Edit` nebo `AddNew` znovu.

##  <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Odstranění záznamu

Odstranění záznamu ze sady záznamů zahrnuje posun na záznam a volání členské funkce [Delete](../../mfc/reference/crecordset-class.md#delete) sady záznamů. Na rozdíl od `AddNew` a `Edit``Delete` nevyžaduje volání `Update`.

Aby byla předběžná podmínka pro volání `Delete`, musí být sada záznamů aktualizovatelná a musí se nacházet na záznamu. Členské funkce `CanUpdate`, `IsBOF`, `IsEOF`a `IsDeleted` umožňují určit tyto podmínky.

Při volání `Delete`:

- Pokud ovladač ODBC podporuje funkci `::SQLSetPos` rozhraní ODBC API, knihovna MFC pomocí funkce odstraní záznam ve zdroji dat. Použití `::SQLSetPos` je obvykle efektivnější než použití SQL.

   \- nebo-

- Pokud `::SQLSetPos` nelze použít, knihovna MFC provede následující akce:

   1. Aktuální záznam v vyrovnávací paměti pro úpravy není zálohován jako v `AddNew` a `Edit`.

   1. `Delete` vytvoří příkaz SQL **Delete** , který odebere záznam.

      Aktuální záznam ve vyrovnávací paměti úprav není uložený jako v `AddNew` a `Edit`.

   1. `Delete` potvrzení odstranění – spustí příkaz **Delete** . Záznam je označen jako odstraněný ve zdroji dat a je-li záznam snímkem, v rozhraní ODBC.

   1. Hodnoty odstraněného záznamu jsou stále v polích datových členů sady záznamů, ale datové členy pole jsou označeny jako null a členská funkce `IsDeleted` sady záznamů vrací nenulovou hodnotu.

   > [!NOTE]
   > Po odstranění záznamu byste se měli posunout na jiný záznam a znovu vyplnit upravenou vyrovnávací paměť daty nového záznamu. Je to chyba při volání `Delete` nebo volání `Edit`.

Informace o příkazech SQL použitých v operacích aktualizace naleznete v tématu [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Další informace o aktualizacích (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)
