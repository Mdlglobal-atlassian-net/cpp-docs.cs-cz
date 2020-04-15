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
ms.openlocfilehash: 0aa9c082d2d04416358d948476f2ae0f9e2a35af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366991"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete vytvořit příjemce ručně.

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje:

- [Vaše role a možnosti při výběru záznamů](#_core_your_options_in_selecting_records).

- [Jak sada záznamů vytvoří svůj příkaz SQL a vybere záznamy](#_core_how_a_recordset_constructs_its_sql_statement).

- [Co můžete udělat pro přizpůsobení výběru](#_core_customizing_the_selection).

Sady záznamů vybírají záznamy ze zdroje dat prostřednictvím ovladače ODBC odesláním příkazů SQL do ovladače. Odeslané SQL závisí na tom, jak navrhnout a otevřít třídu sady záznamů.

## <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a>Vaše možnosti při výběru záznamů

V následující tabulce jsou uvedeny možnosti výběru záznamů.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Jak a kdy můžete ovlivnit sadu záznamů

|Když|Můžeš|
|--------------|-------------|
|Deklarujte třídu sady záznamů pomocí průvodce **Přidat třídu**|Určete, ze které tabulky chcete vybrat.<br /><br /> Určete, které sloupce mají být zahrnuty.<br /><br /> Viz [Přidání příjemce knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Dokončete implementaci třídy sady záznamů|Přepište členské funkce, jako je například `OnSetOptions` (upřesnit) a nastavte možnosti specifické pro aplikaci nebo změňte výchozí hodnoty. Zadejte datové členy parametru, pokud chcete parametrizovanou sadu záznamů.|
|Vytvoření objektu sady záznamů `Open`(před voláním)|Zadejte podmínku hledání (případně složenou) pro použití v klauzuli **WHERE,** která filtruje záznamy. Viz [Sada záznamů: Filtrování záznamů (ODBC).](../../data/odbc/recordset-filtering-records-odbc.md)<br /><br /> Zadejte pořadí řazení pro použití v klauzuli **ORDER BY,** která seřadí záznamy. Viz [Sada záznamů: Řazení záznamů (ODBC).](../../data/odbc/recordset-sorting-records-odbc.md)<br /><br /> Zadejte hodnoty parametrů pro všechny parametry, které jste přidali do třídy. Viz [Sada záznamů: Parametrizace sady záznamů (ODBC).](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)|

| Spuštění dotazu sady záznamů `Open`voláním | Zadejte vlastní řetězec SQL, který nahradí výchozí řetězec SQL nastavený průvodcem. Viz [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) v *referenční příručce knihovny tříd* a [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC).](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

| Volání `Requery` k opětovnému dotazování sady záznamů s nejnovějšími hodnotami ve zdroji dat| Zadejte nové parametry, filtr nebo řazení. Viz [Sada záznamů: Opětovné dotazování sady záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).|

## <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a>Jak sada záznamů konstruuje svůj příkaz SQL

Při volání členské funkce [Open](../../mfc/reference/crecordset-class.md#open) objektu `Open` sady záznamů vytvoří příkaz SQL pomocí některých nebo všech následujících složek:

- Parametr *lpszSQL* byl `Open`předán společnosti . Pokud ne null, tento parametr určuje vlastní řetězec SQL nebo jeho část. Rámec analyzuje řetězec. Pokud je řetězec příkazSQL **SELECT** nebo příkaz ODBC **CALL,** rozhraní framework používá řetězec jako příkaz SQL sady záznamů. Pokud řetězec nezačíná "SELECT" nebo "{CALL", rámci používá co je dodáno k vytvoření klauzule SQL **FROM.**

- Řetězec vrácený [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Ve výchozím nastavení se jedná o název tabulky, kterou jste zadali pro sadu záznamů v průvodci, ale můžete změnit, co funkce vrátí. Rozhraní framework `GetDefaultSQL` volá – pokud řetězec nezačíná "SELECT" nebo "{CALL", předpokládá se, že název tabulky, který se používá k vytvoření řetězce SQL.

- Datové členy pole sady záznamů, které mají být vázány na určité sloupce tabulky. Rozhraní framework váže sloupce záznamu na adresy těchto členů a používá je jako vyrovnávací paměti. Rozhraní framework určuje korelaci členů dat pole se sloupci tabulky z volání funkce [RFX](../../data/odbc/record-field-exchange-using-rfx.md) nebo Bulk RFX v členské funkci [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) sady záznamů.

- Filtr [filter](../../data/odbc/recordset-filtering-records-odbc.md) pro sadu záznamů, pokud existuje, obsažený v [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) datového člena. Rozhraní framework používá tento řetězec k vytvoření klauzule SQL **WHERE.**

- Pořadí [řazení](../../data/odbc/recordset-sorting-records-odbc.md) pro sadu záznamů, pokud existuje, obsažené v [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) datového člena. Rozhraní framework používá tento řetězec k vytvoření klauzule SQL **ORDER BY.**

   > [!TIP]
   > Chcete-li použít klauzuli SQL **GROUP BY** (a případně **klauzuli HAVING),** přidejte klauzule na konec řetězce filtru.

- Hodnoty všech [datových členů parametrů,](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) které zadáte pro třídu. Hodnoty parametrů nastavíte `Open` těsně `Requery`před voláním nebo . Rozhraní framework váže hodnoty parametrů na zástupné symboly "?" v řetězci SQL. V době kompilace zadáte řetězec se zástupnými symboly. Za běhu rozhraní vyplní podrobnosti na základě hodnot parametrů, které předáte.

`Open`vytvoří příkaz SQL **SELECT** z těchto složek. Podrobnosti o tom, jak rámec používá ingredience, najdete v tématu [Přizpůsobení výběru.](#_core_customizing_the_selection)

Po sestavení příkazu `Open` odešle SQL správci ovladačů ODBC (a knihovně kurzorů ODBC, pokud je v paměti), který jej odešle ovladači ODBC pro konkrétní systém DBMS. Ovladač komunikuje s DBMS provést výběr na zdroj dat a načte první záznam. Rozhraní framework načte záznam do datových členů pole sady záznamů.

Kombinaci těchto technik můžete použít k otevření [tabulek](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) a vytvoření dotazu na základě [spojení](../../data/odbc/recordset-performing-a-join-odbc.md) více tabulek. S dalším vlastním nastavením můžete volat předdefinované dotazy (uložené [procedury),](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) vybrat sloupce tabulky, které nejsou v době návrhu známy, a [svázat](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) je s poli sady záznamů nebo můžete provádět většinu dalších úloh přístupu k datům. Úkoly, které nelze provést přizpůsobením sad záznamů, lze stále provádět [voláním funkcí rozhraní API ROZHRANÍ ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) nebo přímým spuštěním příkazů SQL pomocí [cdatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

## <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a>Přizpůsobení výběru

Kromě zadání filtru, pořadí řazení nebo parametrů můžete provést následující akce k přizpůsobení výběru sady záznamů:

- Předat vlastní řetězec SQL v *lpszSQL* při volání [Open](../../mfc/reference/crecordset-class.md#open) pro sadu záznamů. Cokoliv, co předáte v *lpsqSQL,* má přednost před tím, co vrátí členská funkce [GetDefaultSQL.](../../mfc/reference/crecordset-class.md#getdefaultsql)

   Další informace naleznete [v tématu SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC),](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)který popisuje typy příkazů `Open` SQL (nebo částečných příkazů), které můžete předat a co s nimi provádí rozhraní.

    > [!NOTE]
    >  Pokud vlastní řetězec, který předáte, nezačíná "SELECT" nebo "{CALL", knihovna MFC předpokládá, že obsahuje název tabulky. To platí také pro další položku s odrážkami.

- Změňte řetězec, který průvodce zapíše `GetDefaultSQL` do členské funkce sady záznamů. Upravte kód funkce a změňte, co vrátí. Ve výchozím nastavení průvodce `GetDefaultSQL` zapíše funkci, která vrací název jedné tabulky.

   Můžete mít `GetDefaultSQL` vrátit některou z položek, které můžete předat `Open`v *lpszSQL* parametr . Pokud nepředáte vlastní řetězec SQL v *lpszSQL*, `GetDefaultSQL` rozhraní používá řetězec, který vrátí. Musí vrátit `GetDefaultSQL` alespoň jeden název tabulky. Ale můžete mít vrátit více názvů tabulek, úplné **select** prohlášení, příkaz ODBC **CALL** a tak dále. Seznam toho, co můžete předat *lpszSQL* `GetDefaultSQL` – nebo mít return – najdete v článku [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC).](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

   Pokud provádíte spojení dvou nebo více tabulek, přepište `GetDefaultSQL` a přizpůsobte seznam tabulek použitý v klauzuli SQL **FROM.** Další informace naleznete v [tématu Recordset: Provedení spojení (ODBC).](../../data/odbc/recordset-performing-a-join-odbc.md)

- Ručně svázat další členy dat pole, například na základě informací, které získáte o schématu zdroje dat za běhu. Členy dat pole přidáte do třídy sady záznamů, volání funkce [RFX](../../data/odbc/record-field-exchange-using-rfx.md) nebo Bulk RFX do členské funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) a inicializace datových členů v konstruktoru třídy. Další informace naleznete v [tématu Recordset: Dynamicky vazebné datové sloupce (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Přepište členské funkce sady `OnSetOptions`záznamů, například , nastavte možnosti specifické pro aplikaci nebo přepište výchozí hodnoty.

Pokud chcete založit sadu záznamů na komplexní příkaz SQL, je třeba použít některé kombinace těchto technik přizpůsobení. Například možná chcete použít klauzule SQL a klíčová slova, která nejsou přímo podporována sadami záznamů nebo se možná připojujete k více tabulkám.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Základy rozhraní ODBC](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
