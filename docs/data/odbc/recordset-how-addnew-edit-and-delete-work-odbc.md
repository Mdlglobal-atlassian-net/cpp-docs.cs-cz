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
ms.openlocfilehash: 84d4c2f1128f7b73189f69b056eee96619c31ef5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331968"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Sada záznamů: Funkce operací AddNew, Edit a Delete (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak `AddNew`, `Edit`, a `Delete` členské funkce třídy `CRecordset` fungovat. Probíraná témata zahrnují:

- [Jak přidat záznamy](#_core_adding_a_record)

- [Přehled o přidání záznamů](#_core_visibility_of_added_records)

- [Jak funguje Hromadná úprava záznamů](#_core_editing_an_existing_record)

- [Princip odstranění záznamů](#_core_deleting_a_record)

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, přečtěte si téma [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Jako doplněk, můžete chtít číst [výměna polí záznamu: jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md), která popisuje odpovídající role RFX v operacích aktualizace.

##  <a name="_core_adding_a_record"></a> Přidání záznamu

Přidání nového záznamu do sady záznamů zahrnuje volání sady záznamů [AddNew](../../mfc/reference/crecordset-class.md#addnew) členská funkce, nastavení hodnot datové členy nového záznamu a volání [aktualizace](../../mfc/reference/crecordset-class.md#update) členskou funkci pro zápis záznam, který ke zdroji dat.

Podmínkou pro volání `AddNew`, sadě záznamů nesmí být otevřena jen pro čtení. `CanUpdate` a `CanAppend` členské funkce umožňují určit tyto podmínky.

Při volání `AddNew`:

- Záznam ve vyrovnávací paměti pro úpravy je uložen, tak jeho obsah je možné obnovit, pokud operace se zrušila.

- Datové členy polí jsou označeny příznakem, takže je možné zjistit změny v jejich později. Vyčistit data pole, které jsou členy jsou také označené (beze změny) a nastavte na hodnotu Null.

Po zavolání `AddNew`, vyrovnávací paměť pro úpravu představuje nový, prázdný záznam, budete připraveni k vyplní hodnoty. K tomuto účelu ručně nastavte hodnoty tak, že jim přiřadíte. Místo určení hodnoty Skutečná data pro pole, můžete volat `SetFieldNull` zadat hodnotu Null.

Potvrďte provedené změny, můžete volat `Update`. Při volání `Update` pro nový záznam:

- Pokud ovladač rozhraní ODBC podporuje `::SQLSetPos` knihovny MFC rozhraní ODBC API funkce přidat záznam ve zdroji dat pomocí funkce. S `::SQLSetPos`, můžete MFC přidejte záznam efektivněji, protože nemá sestavit a zpracovat příkaz jazyka SQL.

- Pokud `::SQLSetPos` nemůže být použit, MFC, provede následující:

   1. Pokud nejsou nalezeny žádné změny, `Update` neprovede žádnou akci a vrátí hodnotu 0.

   1. Pokud existují změny, `Update` konstrukce SQL **vložit** příkazu. Sloupce reprezentované všechny datové členy nečistých polí jsou uvedeny v **vložit** příkazu. Chcete-li vynutit sloupce mají být zahrnuty, zavolejte [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) členské funkce:

        ```cpp
        SetFieldDirty( &m_dataMember, TRUE );
        ```

   1. `Update` Potvrzení nového záznamu – **vložit** je proveden příkaz a záznam je potvrzen do tabulky zdroje dat (a sady záznamů, pokud není snímek), pokud probíhá transakce.

   1. Uložený záznam se obnoví do vyrovnávací paměti pro úpravy. Záznam, který byl aktuální před `AddNew` volání je aktuální znovu bez ohledu na to, jestli se **vložit** příkazu se provedl úspěšně.

   > [!TIP]
   > Pro úplnou kontrolu nad nový záznam, proveďte následující postup: nastavení hodnot všech polí, které se mají hodnoty a explicitně nastavit všechna pole, která zůstane Null voláním `SetFieldNull` s ukazatelem na pole a parametr PRAVDA (výchozí). Pokud chcete mít jistotu, že pole není zapsána do zdroje dat, zavolejte `SetFieldDirty` s ukazatelem na pole a parametru hodnotu FALSE a nijak nemění hodnoty tohoto pole. Chcete-li zjistit, jestli pole může mít hodnotu Null, zavolejte `IsFieldNullable`.

   > [!TIP]
   > Ke zjištění při změně hodnoty datových členů sady záznamů, knihovna MFC používá hodnotu PSEUDO_NULL na každý datový typ, který můžete uložit do sady záznamů. Pokud pole musíte explicitně nastavit na hodnotu PSEUDO_NULL a pole se stane s již být označeny Null, je nutné volat `SetFieldNull`, předávání na adresu pole v první parametr a hodnotu FALSE ve druhém parametru.

##  <a name="_core_visibility_of_added_records"></a> Přehled o přidání záznamů

Pokud je přidaný záznam viditelné pro sady záznamů? Přidání záznamů v některých případech se zobrazí a někdy se nezobrazí, v závislosti na dvě věci:

- Jaké ovladače je schopen.

- Co rozhraní můžete využít.

Pokud ovladač rozhraní ODBC podporuje `::SQLSetPos` funkce ODBC API, knihovna MFC používá funkci přidat záznamy. S `::SQLSetPos`, přidat záznamy jsou viditelné pro všechny aktualizovat záznamů knihovny MFC. Bez podpory pro funkci přidali záznamy nejsou viditelné a je nutné volat `Requery` k jejich zobrazení. Pomocí `::SQLSetPos` je také mnohem efektivnější.

##  <a name="_core_editing_an_existing_record"></a> Úprava existující záznam

Úprava existující záznam v sadě záznamů zahrnuje posouvání na záznam, volání sady záznamů [upravit](../../mfc/reference/crecordset-class.md#edit) členská funkce, nastavení hodnot datové členy nového záznamu a volání [aktualizovat](../../mfc/reference/crecordset-class.md#update)členskou funkci k zápisu do zdroje dat změněného záznamu.

Podmínkou pro volání `Edit`, aktualizovat a záznamu musí být sada záznamů. `CanUpdate` a `IsDeleted` členské funkce umožňují určit tyto podmínky. Aktuální záznam také nesmí být odstraněný a musí být záznamy v sadě záznamů (obojí `IsBOF` a `IsEOF` vrátí 0).

Při volání `Edit`, záznam ve vyrovnávací paměti pro úpravy (aktuální záznam) je uložen. Záznam uložené hodnoty se později používají ke zjištění, zda pole byly změněny.

Po zavolání `Edit`, vyrovnávací paměť pro úpravu stále představuje aktuální záznam, ale je teď připravený k přijetí změn na pole datové členy. Chcete-li změnit záznamu, ručně nastavit hodnoty žádné datové členy pole, které chcete upravit. Místo určení hodnoty Skutečná data pro pole, můžete volat `SetFieldNull` zadat hodnotu Null. Pro potvrzení změn, volejte `Update`.

> [!TIP]
> Chcete-li získat z `AddNew` nebo `Edit` režimu, volání `Move` s parametrem *AFX_MOVE_REFRESH*.

Podmínkou pro volání `Update`, sadě záznamů nesmí být prázdný a nesmí mít aktuální záznam odstraněn. `IsBOF`, `IsEOF`, a `IsDeleted` by měla vrátit 0.

Při volání `Update` upravovaného záznamu:

- Pokud ovladač rozhraní ODBC podporuje `::SQLSetPos` knihovny MFC rozhraní ODBC API funkce aktualizace záznamu ve zdroji dat pomocí funkce. S `::SQLSetPos`, porovná vaše úpravy vyrovnávací paměti s odpovídající záznam na serveru, aktualizace záznamu na serveru, pokud jsou dva různé ovladač. S `::SQLSetPos`, můžete MFC aktualizovat záznam efektivněji, protože nemá sestavit a zpracovat příkaz jazyka SQL.

   \- nebo –

- Pokud `::SQLSetPos` nemůže být použit, MFC, provede následující:

   1. Pokud zde nejsou žádné změny `Update` neprovede žádnou akci a vrátí hodnotu 0.

   1. Pokud existují změny, `Update` konstrukce SQL **aktualizace** příkazu. Sloupce uvedené v **aktualizace** příkazu jsou založeny na datové členy polí, které se změnily.

   1. `Update` potvrdí změny – provede **aktualizace** příkaz – záznam se změní na zdroj dat, ale není potvrzená, pokud transakce je v průběhu (naleznete v tématu [transakce: provádění transakcí v sadě záznamů (rozhraní ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) informace o tom, jak transakce ovlivňuje aktualizace). Rozhraní ODBC uchovává kopii tohoto záznamu, který se také změní.

   1. Na rozdíl od procesu pro `AddNew`, `Edit` procesu neobnoví uložený záznam. Upravený záznam zůstává na místě jako aktuální záznam.

   > [!CAUTION]
   > Při přípravě na sadu záznamů aktualizovat pomocí volání `Update`, Upozorňujeme, že vaše sada záznamů obsahuje všechny sloupce, které tvoří primární klíč tabulky (nebo všechny sloupce jakýkoli jedinečný index pro tabulku nebo dostatek sloupců k jednoznačné identifikaci řádek). V některých případech můžete použít rozhraní pouze vybrané sloupce ve vaší sadě záznamů pro identifikaci, který záznam v tabulce k aktualizaci. Bez všech potřebných sloupců může být aktualizován více záznamů v tabulce. V tomto případě rozhraní vyvolá výjimky při volání `Update`.

   > [!TIP]
   > Při volání `AddNew` nebo `Edit` po zavolání funkce dřív, ale před volání `Update`, aktualizují se uložené záznam nahrazení nové nebo upravené záznamu v průběhu vyrovnávací paměť pro úpravu. Toto chování poskytuje způsob, jak přerušení `AddNew` nebo `Edit` a zahájit novou: Pokud zjistíte, že záznam v průběhu chybný, jednoduše zavolejte `Edit` nebo `AddNew` znovu.

##  <a name="_core_deleting_a_record"></a> Odstranění záznamu

Odstranění záznamu z sady záznamů zahrnuje posouvání na záznam a volání sady záznamů [odstranit](../../mfc/reference/crecordset-class.md#delete) členskou funkci. Na rozdíl od `AddNew` a `Edit`, `Delete` nevyžaduje odpovídající volání `Update`.

Podmínkou pro volání `Delete`, třeba umožnit aktualizaci modelové sady záznamů a musí být na záznam. `CanUpdate`, `IsBOF`, `IsEOF`, A `IsDeleted` členské funkce umožňují určit tyto podmínky.

Při volání `Delete`:

- Pokud ovladač rozhraní ODBC podporuje `::SQLSetPos` funkce ODBC API, knihovna MFC odstranění záznamu ve zdroji dat pomocí funkce. Pomocí `::SQLSetPos` obvykle je efektivnější než při použití SQL.

   \- nebo –

- Pokud `::SQLSetPos` nemůže být použit, MFC, provede následující:

   1. Aktuální záznam ve vyrovnávací paměti úpravy se nezálohovují jako v `AddNew` a `Edit`.

   1. `Delete` vytvoří SQL **odstranit** příkaz, který odstraní záznam.

      Aktuální záznam ve vyrovnávací paměti úpravy není uložen jako v `AddNew` a `Edit`.

   1. `Delete` potvrzení odstranění – provede **odstranit** příkazu. Záznam je označen odstraněný zdroj dat, a pokud záznamu snímku, v rozhraní ODBC.

   1. Odstraněný záznam hodnoty jsou stále v datové členy polí sady záznamů, ale datové členy polí jsou označeny Null a sady záznamů `IsDeleted` členská funkce vrátí nenulovou hodnotu.

   > [!NOTE]
   > Po odstranění záznamu, byste měli přejít na jiný záznam pro doplňování vyrovnávací paměti pro úpravy s daty v novém záznamu. Jedná se o chybu volání `Delete` znovu nebo volat `Edit`.

Informace o dotazech SQL použitých v operacích aktualizace najdete v tématu [SQL](../../data/odbc/sql.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Další informace o aktualizacích (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)<br/>
[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)