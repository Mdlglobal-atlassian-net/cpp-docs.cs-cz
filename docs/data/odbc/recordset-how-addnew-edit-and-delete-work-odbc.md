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
ms.openlocfilehash: 63718a6be3a9ce19ddbce923a84def21448c42a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367006"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Sada záznamů: Funkce operací AddNew, Edit a Delete (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

`AddNew`Toto téma vysvětluje, `Edit`jak `Delete` fungují funkce `CRecordset` , a členské funkce třídy. Probíraná témata zahrnují:

- [Jak funguje přidávání záznamů](#_core_adding_a_record)

- [Viditelnost přidaných záznamů](#_core_visibility_of_added_records)

- [Jak funguje úpravy záznamů](#_core_editing_an_existing_record)

- [Jak funguje odstranění záznamů](#_core_deleting_a_record)

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na objekty odvozené od, ve kterém hromadné načítání řádků nebyla implementována. Pokud používáte hromadné načítání řádků, přečtěte si část [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Jako doplněk můžete chtít číst [Záznam Field Exchange: Jak RFX works](../../data/odbc/record-field-exchange-how-rfx-works.md), který popisuje odpovídající roli RFX v operacích aktualizace.

## <a name="adding-a-record"></a><a name="_core_adding_a_record"></a>Přidání záznamu

Přidání nového záznamu do sady záznamů zahrnuje volání členské funkce [AddNew](../../mfc/reference/crecordset-class.md#addnew) sady záznamů, nastavení hodnot datových členů pole nového záznamu a volání členské funkce [Update](../../mfc/reference/crecordset-class.md#update) k zápisu záznamu do zdroje dat.

Jako předpoklad pro `AddNew`volání sada záznamů nesmí být otevřena jako jen pro čtení. A `CanUpdate` `CanAppend` členské funkce umožňují určit tyto podmínky.

Když voláte: `AddNew`

- Záznam ve vyrovnávací paměti pro úpravy je uložen, takže jeho obsah lze obnovit, pokud je operace zrušena.

- Datové členy pole jsou označeny příznakem, takže je možné zjistit změny v nich později. Datové členy pole jsou také označeny jako čisté (beze změny) a nastaveny na hodnotu Null.

Po volání `AddNew`představuje editační vyrovnávací paměť nový prázdný záznam připravený k vyplnění hodnotami. Chcete-li to provést, ručně nastavte hodnoty přiřazením k nim. Místo určení skutečné hodnoty dat pro pole můžete `SetFieldNull` volat a zadat hodnotu Null.

Chcete-li potvrdit změny, volejte `Update`. Při volání `Update` o nový záznam:

- Pokud ovladač ROZHRANÍ ODBC podporuje funkci `::SQLSetPos` ROZHRANÍ API ROZHRANÍ ODBC, knihovna MFC tuto funkci použije k přidání záznamu do zdroje dat. Pomocí `::SQLSetPos`knihovny MFC můžete přidat záznam efektivněji, protože není nutné vytvářet a zpracovávat příkaz SQL.

- Pokud `::SQLSetPos` nelze použít, knihovna MFC provede následující:

   1. Pokud nejsou zjištěny `Update` žádné změny, neprovede žádnou akci a vrátí hodnotu 0.

   1. Pokud dojde ke `Update` změnám, vytvoří příkaz SQL **INSERT.** Sloupce reprezentované všemi členy dat dirty pole jsou uvedeny v **příkazu INSERT.** Chcete-li vynutit zahrnutí sloupce, zavolejte členní funkci [SetFieldDirty:](../../mfc/reference/crecordset-class.md#setfielddirty)

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update`potvrdí nový záznam – příkaz **INSERT** je proveden a záznam je potvrzen do tabulky ve zdroji dat (a sada záznamů, ne-li snímek), pokud transakce probíhá.

   1. Uložený záznam je obnoven do vyrovnávací paměti pro úpravy. Záznam, který byl `AddNew` aktuální před voláním je aktuální znovu bez ohledu na to, zda **insert** příkaz byl úspěšně proveden.

   > [!TIP]
   > Chcete-li získat úplnou kontrolu nad novým záznamem, postupujte takto: nastavte hodnoty všech polí, `SetFieldNull` která budou mít hodnoty, a pak explicitně nastavte všechna pole, která zůstanou null, voláním s ukazatelem na pole a parametrem TRUE (výchozí). Chcete-li zajistit, aby pole nebylo zapsáno do `SetFieldDirty` zdroje dat, zavolejte ukazatelem na pole a parametr NEPRAVDA a neupravujte hodnotu pole. Chcete-li zjistit, zda je povoleno `IsFieldNullable`mít pole hodnotu Null, volejte .

   > [!TIP]
   > Chcete-li zjistit, kdy změní hodnotu datových členů sady záznamů, použije knihovna MFC PSEUDO_NULL hodnotu odpovídající každému datovému typu, který lze uložit do sady záznamů. Pokud je nutné explicitně nastavit pole na hodnotu PSEUDO_NULL a pole, `SetFieldNull`které již má být označeno jako null, musíte také zavolat , předat adresu pole v prvním parametru a FALSE v druhém parametru.

## <a name="visibility-of-added-records"></a><a name="_core_visibility_of_added_records"></a>Viditelnost přidaných záznamů

Kdy je přidaný záznam viditelný pro vaši sadu záznamů? Přidané záznamy se někdy zobrazují a někdy nejsou viditelné v závislosti na dvou věcech:

- Čeho je váš řidič schopen.

- Co framework může využít.

Pokud ovladač ROZHRANÍ ODBC podporuje funkci `::SQLSetPos` ROZHRANÍ API ROZHRANÍ ODBC, knihovna MFC tuto funkci používá k přidání záznamů. S `::SQLSetPos`, přidané záznamy jsou viditelné pro všechny aktualizovatelné sady záznamů knihovny MFC. Bez podpory funkce nejsou přidané záznamy viditelné a `Requery` je nutné volat, abyste je viděli. Použití `::SQLSetPos` je také efektivnější.

## <a name="editing-an-existing-record"></a><a name="_core_editing_an_existing_record"></a>Úprava existujícího záznamu

Úprava existujícího záznamu v sadě záznamů zahrnuje posouvání na záznam, volání členské funkce [Edit](../../mfc/reference/crecordset-class.md#edit) sady záznamů, nastavení hodnot datových členů pole nového záznamu a volání členské funkce [Update](../../mfc/reference/crecordset-class.md#update) k zápisu změněného záznamu do zdroje dat.

Jako předpoklad pro `Edit`volání musí být sada záznamů aktualizovatelná a v záznamu. A `CanUpdate` `IsDeleted` členské funkce umožňují určit tyto podmínky. Aktuální záznam také nesmí být odstraněn a v sadě záznamů musí `IsBOF` být `IsEOF` záznamy (oba a vrátí 0).

Při volání `Edit`je záznam uložen v editační vyrovnávací paměti (aktuální záznam). Hodnoty uloženého záznamu se později používají ke zjištění, zda se některá pole změnila.

Po volání `Edit`představuje vyrovnávací paměť pro úpravy stále aktuální záznam, ale nyní je připravena přijmout změny datových členů pole. Chcete-li záznam změnit, nastavte ručně hodnoty všech datových členů pole, které chcete upravit. Místo určení skutečné hodnoty dat pro pole můžete `SetFieldNull` volat a zadat hodnotu Null. Chcete-li změny `Update`potvrdit, zavolejte .

> [!TIP]
> Chcete-li `AddNew` se `Edit` dostat `Move` ven nebo režimu, volejte s parametrem *AFX_MOVE_REFRESH*.

Jako předpoklad pro `Update`volání nesmí být sada záznamů prázdná a aktuální záznam nesmí být odstraněn. `IsBOF`, `IsEOF`a `IsDeleted` všechny by měly vrátit 0.

Při volání `Update` upraveného záznamu:

- Pokud ovladač ROZHRANÍ ODBC podporuje funkci `::SQLSetPos` ROZHRANÍ API ROZHRANÍ ODBC, knihovna MFC tuto funkci použije k aktualizaci záznamu ve zdroji dat. Pomocí `::SQLSetPos`aplikace porovná ovladač vyrovnávací paměť pro úpravy s odpovídajícím záznamem na serveru a aktualizuje záznam na serveru, pokud se tyto dva soubory liší. Pomocí `::SQLSetPos`knihovny MFC lze aktualizovat záznam efektivněji, protože není nutné vytvářet a zpracovávat příkaz SQL.

   \-nebo -

- Pokud `::SQLSetPos` nelze použít, knihovna MFC provede následující:

   1. Pokud nedošlo k žádné `Update` změny, neprovede žádnou akci a vrátí 0.

   1. Pokud dojde ke `Update` změnám, vytvoří příkaz SQL **UPDATE.** Sloupce uvedené v příkazu **UPDATE** jsou založeny na datových členech pole, které se změnily.

   1. `Update`potvrdí změny – provede **příkaz UPDATE** – a záznam se změní na zdroj dat, ale není potvrzena, pokud transakce probíhá (viz [Transakce: Provedení transakce v recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) informace o tom, jak transakce ovlivňuje aktualizaci). Rozhraní ODBC uchovává kopii záznamu, která se také mění.

   1. Na rozdíl `AddNew`od `Edit` procesu pro , proces neobnoví uložený záznam. Upravený záznam zůstane na místě jako aktuální záznam.

   > [!CAUTION]
   > Při přípravě na aktualizaci `Update`sady záznamů voláním , dbát na to, aby vaše sada záznamů obsahuje všechny sloupce tvoří primární klíč tabulky (nebo všechny sloupce libovolného jedinečného indexu v tabulce nebo dostatek sloupců k jednoznačné identifikaci řádku). V některých případech může rozhraní framework použít pouze sloupce vybrané v sadě záznamů k identifikaci záznamu v tabulce k aktualizaci. Bez všech potřebných sloupců může být v tabulce aktualizováno více záznamů. V tomto případě rozhraní framework vyvolá výjimky při volání `Update`.

   > [!TIP]
   > Pokud `AddNew` zavoláte `Edit` nebo zavoláte jednu z `Update`funkcí dříve, ale před voláním , bude vyrovnávací paměť úprav aktualizována uloženým záznamem a nahradí se nový nebo upravený záznam. Toto chování umožňuje přerušit `AddNew` nebo `Edit` a začít nový: pokud zjistíte, že záznam v průběhu `Edit` je `AddNew` vadný, jednoduše volat nebo znovu.

## <a name="deleting-a-record"></a><a name="_core_deleting_a_record"></a>Odstranění záznamu

Odstranění záznamu ze sady záznamů zahrnuje posouvání na záznam a volání členské funkce [Delete](../../mfc/reference/crecordset-class.md#delete) sady záznamů. Na `AddNew` `Edit`rozdíl `Delete` od a , `Update`nevyžaduje odpovídající volání .

Jako předpoklad pro `Delete`volání musí být sada záznamů aktualizovatelná a musí být v záznamu. Funkce `CanUpdate` `IsBOF`, `IsEOF`a `IsDeleted` členské umožňují určit tyto podmínky.

Když voláte: `Delete`

- Pokud ovladač ROZHRANÍ ODBC podporuje funkci `::SQLSetPos` ROZHRANÍ API ROZHRANÍ ODBC, knihovna MFC tuto funkci použije k odstranění záznamu ve zdroji dat. Použití `::SQLSetPos` je obvykle efektivnější než použití SQL.

   \-nebo -

- Pokud `::SQLSetPos` nelze použít, knihovna MFC provede následující:

   1. Aktuální záznam ve vyrovnávací paměti pro úpravy `AddNew` `Edit`není zálohován jako v a .

   1. `Delete`vytvoří příkaz SQL **DELETE,** který odebere záznam.

      Aktuální záznam ve vyrovnávací paměti pro `AddNew` úpravy není uložen jako v aplikaci a . `Edit`

   1. `Delete`potvrdí odstranění – provede **příkaz DELETE.** Záznam je označen odstraněn ve zdroji dat a pokud je záznam snímek, v rozhraní ODBC.

   1. Hodnoty odstraněného záznamu jsou stále v datových členech pole sady záznamů, ale datové členy `IsDeleted` pole jsou označeny jako null a členská funkce sady záznamů vrátí nenulovou hodnotu.

   > [!NOTE]
   > Po odstranění záznamu byste se měli posunout na jiný záznam a znovu vyplnit vyrovnávací paměť úprav daty nového záznamu. Je chyba volat `Delete` znovu nebo `Edit`volání .

Informace o příkazech SQL používaných v operacích aktualizace naleznete v tématu [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Další informace o aktualizacích (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)
