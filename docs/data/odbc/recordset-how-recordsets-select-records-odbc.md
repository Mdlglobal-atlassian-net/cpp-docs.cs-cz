---
title: 'Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 252d17fc56c13415f1068d6b16ed8b1ee663b5f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212885"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje:

- [Vaše role a možnosti v rámci výběru záznamů](#_core_your_options_in_selecting_records).

- [Způsob, jakým sada záznamů vytvoří svůj příkaz SQL a vybere záznamy](#_core_how_a_recordset_constructs_its_sql_statement).

- [Co můžete udělat pro přizpůsobení výběru](#_core_customizing_the_selection).

Sady záznamů vybírají záznamy ze zdroje dat prostřednictvím ovladače ODBC odesláním příkazů SQL do ovladače. Odeslání SQL závisí na tom, jak navrhujete a otevíráte třídu sady záznamů.

##  <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a>Vaše možnosti při výběru záznamů

V následující tabulce jsou uvedené možnosti pro výběr záznamů.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Jak a kdy můžete ovlivnit sadu záznamů

|Při|Můžeš|
|--------------|-------------|
|Deklarace třídy sady záznamů pomocí průvodce **přidáním třídy**|Určete, ze které tabulky se má vybírat.<br /><br /> Zadejte sloupce, které chcete zahrnout.<br /><br /> Viz [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Dokončení implementace třídy sady záznamů|Přepsat členské funkce, například `OnSetOptions` (rozšířené) pro nastavení možností specifických pro aplikaci nebo změna výchozích hodnot. Určete datové členy parametru, pokud chcete parametrizovanou sadu záznamů.|
|Konstrukce objektu sady záznamů (před voláním `Open`)|Zadejte podmínku vyhledávání (případně složenou) pro použití v klauzuli **WHERE** , která filtruje záznamy. Viz [Sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Zadejte pořadí řazení pro použití v klauzuli **ORDER by** , která Seřadí záznamy. Viz [Sada záznamů: řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Zadejte hodnoty parametrů pro všechny parametry, které jste přidali do třídy. Viz [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

| Spusťte dotaz sady záznamů voláním `Open`| Zadejte vlastní řetězec SQL, který nahradí výchozí řetězec SQL nastavený průvodcem. Viz [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) v *knihovně tříd reference* a [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |

| Zavolejte `Requery` pro opětovné spuštění dotazu sady záznamů s nejnovějšími hodnotami ve zdroji dat | Zadejte nové parametry, filtr nebo řazení. Viz [Sada záznamů: dotazování sady záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |

##  <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a>Jak sada záznamů vytvoří svůj příkaz SQL

Při volání [otevřené](../../mfc/reference/crecordset-class.md#open) členské funkce objektu sady záznamů `Open` sestaví příkaz SQL pomocí některých nebo všech následujících složek:

- Parametr *lpszSQL* předaný `Open`. Pokud hodnota není NULL, tento parametr určuje vlastní řetězec SQL nebo část jednoho. Rozhraní analyzuje řetězec. Pokud je řetězec příkazem SQL **Select** nebo příkazem **volání** ODBC, rozhraní používá řetězec jako příkaz SQL sady záznamů. Pokud řetězec nezačíná "SELECT" nebo "{CALL", rozhraní používá rozhraní, které je dodáno k vytvoření klauzule SQL **from** .

- Řetězec vrácený funkcí [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Ve výchozím nastavení je to název tabulky, kterou jste zadali pro sadu záznamů v průvodci, ale můžete změnit, co funkce vrátí. Rozhraní volá `GetDefaultSQL` – Pokud řetězec nezačíná "SELECT" nebo "{CALL", předpokládá se, že se jedná o název tabulky, který se používá k vytvoření řetězce SQL.

- Pole datových členů sady záznamů, které mají být vázány na konkrétní sloupce tabulky. Rozhraní váže sloupce záznamů na adresy těchto členů a použije je jako vyrovnávací paměti. Rozhraní určuje korelaci datových členů pole k tabulkovým sloupcům z volání funkce [RFX](../../data/odbc/record-field-exchange-using-rfx.md) nebo Bulk RFX v rámci funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) členské funkce sady záznamů.

- [Filtr](../../data/odbc/recordset-filtering-records-odbc.md) pro sadu záznamů, pokud existuje, obsažený v [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) datovém členu. Rozhraní používá tento řetězec k vytvoření klauzule **WHERE** jazyka SQL.

- Pořadí [řazení](../../data/odbc/recordset-sorting-records-odbc.md) pro sadu záznamů, pokud existuje, obsažena v datovém členu [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) . Rozhraní používá tento řetězec k vytvoření klauzule **ORDER by** SQL.

   > [!TIP]
   > Chcete-li použít klauzuli **Group by** (případně klauzuli **having** ), přidejte klauzule na konec řetězce filtru.

- Hodnoty všech [datových členů parametrů](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) , které zadáte pro třídu. Hodnoty parametrů nastavíte těsně před voláním `Open` nebo `Requery`. Rozhraní váže hodnoty parametrů k zástupným symbolům "?" v řetězci SQL. V době kompilace zadáte řetězec se zástupnými symboly. V době běhu rozhraní vyplní podrobnosti na základě hodnot parametrů, které předáte.

`Open` vytvoří příkaz SQL **Select** z těchto složek. Podrobnosti o tom, jak rozhraní používá tyto komponenty, najdete v tématu [přizpůsobení výběru](#_core_customizing_the_selection) .

Po vytvoření příkazu `Open` odešle SQL do správce ovladačů ODBC (a do knihovny kurzorů rozhraní ODBC, pokud je v paměti), která ho pošle ovladači ODBC pro konkrétní DBMS. Ovladač komunikuje s DBMS a provede výběr na zdroji dat a načte první záznam. Rozhraní načte záznam do datových členů pole sady záznamů.

Kombinaci těchto postupů můžete použít k otevření [tabulek](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) a k vytvoření dotazu na základě [spojení](../../data/odbc/recordset-performing-a-join-odbc.md) více tabulek. Pomocí dalšího přizpůsobení můžete volat [předdefinované dotazy](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (uložené procedury), vybrat sloupce tabulky, které nejsou v době návrhu známy, a [vytvořit jejich vazby](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) k polím sady záznamů nebo můžete provést většinu dalších úloh přístupu k datům. Úkoly, které nemůžete provést přizpůsobením sad záznamů, se dají provést [voláním funkcí rozhraní ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) nebo přímo vykonávajícími příkazy SQL pomocí [CDatabase:: ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

##  <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a>Přizpůsobení výběru

Kromě poskytnutí filtru, pořadí řazení nebo parametry můžete provést následující akce pro přizpůsobení výběru vaší sady záznamů:

- Předat vlastní řetězec SQL v *lpszSQL* při volání metody [Open](../../mfc/reference/crecordset-class.md#open) pro sadu záznamů. Cokoli, co předáte v *lpsqSQL* , má přednost před tím, co vrací členskou funkci [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) .

   Další informace naleznete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), který popisuje typy příkazů SQL (nebo částečné příkazy), které lze předat `Open` a k čemu rozhraní s nimi.

    > [!NOTE]
    >  Pokud vlastní řetězec, který předáte, nezačíná "SELECT" nebo "{CALL", knihovna MFC předpokládá, že obsahuje název tabulky. To platí i pro další položku s odrážkami.

- Upravte řetězec, který průvodce zapíše do `GetDefaultSQL` členské funkce vaší sady záznamů. Úpravou kódu funkce změňte, co vrátí. Ve výchozím nastavení průvodce zapíše funkci `GetDefaultSQL`, která vrací název jedné tabulky.

   Můžete mít `GetDefaultSQL` vrátit libovolnou z položek, které lze předat v parametru *lpszSQL* pro `Open`. Pokud nepředáte vlastní řetězec SQL v *lpszSQL*, rozhraní používá řetězec, který `GetDefaultSQL` vrátí. Minimálně `GetDefaultSQL` musí vracet název jedné tabulky. Můžete ale mít možnost vracet více názvů tabulek, úplný příkaz **Select** , příkaz **volání** rozhraní ODBC a tak dále. Seznam toho, co můžete předat *lpszSQL* , nebo `GetDefaultSQL` vrátit, najdete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

   Provádíte-li spojení dvou nebo více tabulek, přepište `GetDefaultSQL` pro přizpůsobení seznamu tabulek používaného v klauzuli SQL **from** . Další informace naleznete v tématu [Sada záznamů: provádí se spojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Ruční vazba dalších datových členů pole, možná na základě informací, které získáte o schématu zdroje dat v době běhu. Přidáte datové členy pole do třídy sady záznamů, [RFX](../../data/odbc/record-field-exchange-using-rfx.md) nebo hromadné volání funkce RFX pro ně do členské funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) a inicializací datových členů v konstruktoru třídy. Další informace naleznete v tématu [Sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Přepsat členské funkce sady záznamů, například `OnSetOptions`, pro nastavení možností specifických pro aplikaci nebo přepsání výchozích hodnot.

Pokud chcete vytvořit založit sadu záznamů v komplexním příkazu SQL, je nutné použít několik kombinací těchto technik přizpůsobení. Například možná budete chtít použít klauzule SQL a klíčová slova, která nejsou přímo podporována sadami záznamů, nebo možná se připojujete k několika tabulkám.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[ODBC – základy](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
