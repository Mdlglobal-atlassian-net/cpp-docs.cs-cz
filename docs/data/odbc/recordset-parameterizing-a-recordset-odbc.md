---
title: 'Sada záznamů: Parametrizace sady záznamů (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: 6d28471bdc44d5d75a9eeac2327f92a8e2e265c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360663"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Sada záznamů: Parametrizace sady záznamů (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Někdy můžete chtít vybrat záznamy za běhu pomocí informací, které jste vypočítali nebo získali od koncového uživatele. Parametry sady záznamů umožňují dosáhnout tohoto cíle.

Toto téma vysvětluje:

- [Účel parametrizované sady záznamů](#_core_parameterized_recordsets).

- [Kdy a proč můžete chtít parametrizovat sadu záznamů](#_core_when_to_use_parameters).

- [Jak deklarovat datové členy parametrů ve třídě sady záznamů](#_core_parameterizing_your_recordset_class).

- [Jak předat informace o parametrech do objektu sady záznamů za běhu](#_core_passing_parameter_values_at_run_time).

## <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a>Parametrizované sady záznamů

Parametrizovaná sada záznamů umožňuje předávat informace o parametrech za běhu. To má dva cenné účinky:

- Mohlo by to mít za následek lepší rychlost provádění.

- Umožňuje vytvořit dotaz za běhu na základě informací, které nejsou k dispozici v době návrhu, jako jsou informace získané od uživatele nebo vypočtené za běhu.

Při volání `Open` ke spuštění dotazu sada záznamů používá informace o parametru k dokončení jeho **SQL SELECT** příkaz. Můžete parametrizovat libovolnou sadu záznamů.

## <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a>Kdy použít parametry

Mezi typické použití parametrů patří:

- Předávání argumentů za běhu předdefinovanému dotazu.

   Chcete-li předat parametry uložené proceduře, musíte zadat úplný vlastní příkaz ODBC **CALL** – s zástupnými symboly parametrů – při volání `Open`, přepsání výchozího příkazu SQL sady záznamů. Další informace naleznete v [tématu CRecordset::Open](../../mfc/reference/crecordset-class.md#open) in the *Class Library Reference* and [SQL: Customizing Your Recordset's SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) and [Recordset: Declaring a Class for a Predefined Query (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Efektivní provádění mnoha requeries s různými informacemi o parametrech.

   Například pokaždé, když koncový uživatel vyhledá informace o konkrétním studentovi v databázi registrace studentů, můžete zadat jméno studenta nebo ID jako parametr získaný od uživatele. Když pak zavoláte člennou `Requery` funkci sady záznamů, dotaz vybere pouze záznam tohoto studenta.

   Řetězec filtru sady záznamů, uložený v `m_strFilter`aplikaci , může vypadat takto:

    ```cpp
    "StudentID = ?"
    ```

   Předpokládejme, že v proměnné `strInputID`získáte ID studenta . Když nastavíte `strInputID` parametr na (například ID studenta 100), hodnota proměnné je vázána na zástupný symbol parametru reprezentovaný "?" v řetězci filtru.

   Přiřaďte hodnotu parametru takto:

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   Chcete nastavit řetězec filtru tímto způsobem:

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Diskuse o správném použití uvozovek pro řetězce filtrů naleznete v tématu [Recordset: Filtering Records (ODBC).](../../data/odbc/recordset-filtering-records-odbc.md)

   Hodnota parametru se liší pokaždé, když znovu zadávací dotaz na sadu záznamů pro nové ID studenta.

   > [!TIP]
   > Použití parametru je efektivnější než pouhé filtrování. Pro parametrizovanou sadu záznamů musí databáze zpracovat příkaz SQL **SELECT** pouze jednou. U filtrované sady záznamů bez **SELECT** parametrů musí být příkaz SELECT `Requery` zpracován pokaždé, když s novou hodnotou filtru.

Další informace o filtrech naleznete v [tématu Recordset: Filtering Records (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

## <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a>Parametrizace třídy sady záznamů

> [!NOTE]
> Tato část se vztahuje na `CRecordset` objekty odvozené od, ve kterém hromadné načítání řádku nebyla implementována. Pokud používáte hromadné načítání řádků, implementace parametrů je podobný proces. Další informace naleznete [v tématu Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Před vytvořením třídy sady záznamů určete, jaké parametry potřebujete, jaké jsou jejich datové typy a jak je sada záznamů používá.

#### <a name="to-parameterize-a-recordset-class"></a>Parametrizaci třídy sady záznamů

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Tuto funkci můžete stále vytvořit ručně.

1. Spusťte [Průvodce vytvářením knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **přidat třídu** a vytvořte třídu.

1. Zadejte datové členy pole pro sloupce sady záznamů.

1. Poté, co průvodce zapíše třídu do souboru v projektu, přejděte do souboru H a ručně přidejte jeden nebo více datových členů parametru do deklarace třídy. Přidání může vypadat podobně jako v následujícím příkladu, část třídy snímek určené k odpovědi na dotaz "Kteří studenti jsou ve třídě senior?"

    ```cpp
    class CStudentSet : public CRecordset
    {
    // Field/Param Data
        CString m_strFirstName;
        CString m_strLastName;
        CString m_strStudentID;
        CString m_strGradYear;

        CString m_strGradYrParam;
    };
    ```

   Přidejte datové členy parametrů za datové členy pole generované průvodcem. Konvence je připojit slovo "Param" ke každému uživatelem definovanému názvu parametru.

1. Upravte definici členské funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) v souboru CPP. Přidejte volání funkce RFX pro každý datový člen parametru, který jste přidali do třídy. Informace o psaní funkcí RFX naleznete v [tématu Záznam pole Exchange: Jak RFX funguje](../../data/odbc/record-field-exchange-how-rfx-works.md). Před volání rfx pro parametry s jedním voláním:

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. V konstruktoru třídy sady záznamů se počet parametrů `m_nParams`zintáčkem .

   Další informace naleznete [v tématu Záznam v poli Exchange: Práce s kódem průvodce](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Při psaní kódu, který vytvoří objekt sady záznamů této třídy, umístěte "?" (otazník) symbol na každém místě v řetězci příkazu SQL, kde má být parametr nahrazen.

   Za běhu jsou zástupné symboly "?" vyplněny v pořadí předanými hodnotami parametrů. První sada datových členů parametru po volání [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) nahradí první "?" v řetězci SQL, druhý datový člen parametru nahradí druhý "?", a tak dále.

> [!NOTE]
> Pořadí parametrů je důležité: pořadí RFX volání `DoFieldExchange` parametrů ve vaší funkci musí odpovídat pořadí zástupných symbolů parametrů v řetězci SQL.

> [!TIP]
> Nejpravděpodobnější řetězec pro práci s je řetězec, který zadáte (pokud existuje) pro [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) datového člena třídy, ale některé ovladače ODBC může povolit parametry v jiných klauzulích SQL.

## <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a>Předávání hodnot parametrů za běhu

Před voláním `Open` (pro nový objekt sady záznamů) `Requery` nebo (pro existující objekt) je nutné zadat hodnoty parametrů.

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Předání hodnot parametrů objektu sady záznamů za běhu

1. Vytvořte objekt sady záznamů.

1. Připravte řetězec nebo řetězce, `m_strFilter` jako je například řetězec, obsahující příkaz SQL nebo jeho části. Umístěte zástupné symboly "?" tam, kam mají být vloženy informace o parametru.

1. Každému datovému členu parametru parametru objektu přiřaďte hodnotu parametru run-time.

1. Volání `Open` členské funkce `Requery`(nebo , pro existující sadu záznamů).

Předpokládejme například, že chcete zadat řetězec filtru pro sadu záznamů pomocí informací získaných za běhu. Předpokládejme, že jste vytvořili `CStudentSet` sadu `rsStudents` záznamů třídy dříve - volal - a nyní chcete requery pro určitý druh informací o studentovi.

```cpp
// Set up a filter string with
// parameter placeholders
rsStudents.m_strFilter = "GradYear <= ?";

// Obtain or calculate parameter values
// to pass--simply assigned here
CString strGradYear = GetCurrentAcademicYear( );

// Assign the values to parameter data members
rsStudents.m_strGradYrParam = strGradYear;

// Run the query
if( !rsStudents.Requery( ) )
    return FALSE;
```

Sada záznamů obsahuje záznamy pro studenty, jejichž záznamy splňují podmínky určené filtrem, který byl vytvořen z parametrů za běhu. V tomto případě sada záznamů obsahuje záznamy pro všechny starší studenty.

> [!NOTE]
> V případě potřeby můžete nastavit hodnotu datového člena parametru na hodnotu Null pomocí [funkce SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Můžete také zkontrolovat, zda je datový člen parametru Null pomocí [isfieldnull](../../mfc/reference/crecordset-class.md#isfieldnull).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)
