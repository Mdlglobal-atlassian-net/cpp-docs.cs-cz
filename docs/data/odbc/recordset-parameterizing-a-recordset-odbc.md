---
title: 'Sada záznamů: Parametrizace sady záznamů (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: eaf95312b73b5165d64de7f9ded95db29d8909d0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075820"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Sada záznamů: Parametrizace sady záznamů (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Někdy je možné, že budete chtít vybrat záznamy za běhu s použitím informací, které jste vypočítali nebo získali od koncového uživatele. Parametry sady záznamů umožňují dosáhnout tohoto cíle.

Toto téma vysvětluje:

- [Účel parametrizované sady záznamů](#_core_parameterized_recordsets).

- [Kdy a proč možná budete chtít parametrizovat sadu záznamů](#_core_when_to_use_parameters).

- [Postup deklarace datových členů parametrů ve třídě sady záznamů](#_core_parameterizing_your_recordset_class).

- [Jak předat informace o parametrech do objektu sady záznamů v době běhu](#_core_passing_parameter_values_at_run_time).

##  <a name="parameterized-recordsets"></a><a name="_core_parameterized_recordsets"></a>Parametrizované sady záznamů

Parametrizovaná sada záznamů umožňuje předat informace o parametrech v době běhu. To má dva cenné účinky:

- Může to mít za následek lepší rychlost spuštění.

- Umožňuje sestavovat dotaz za běhu, a to na základě informací, které nejsou k dispozici v době návrhu, jako jsou například informace získané od uživatele nebo vypočítané v době běhu.

Když zavoláte `Open` pro spuštění dotazu, sada záznamů použije informace o parametrech k dokončení příkazu **SQL SELECT** . Můžete parametrizovat libovolnou sadu záznamů.

##  <a name="when-to-use-parameters"></a><a name="_core_when_to_use_parameters"></a>Kdy použít parametry

Mezi Typická použití pro parametry patří:

- Předávání argumentů za běhu do předdefinovaného dotazu.

   Chcete-li předat parametry uložené proceduře, je nutné zadat úplný vlastní příkaz **volání** rozhraní ODBC – se zástupnými symboly parametrů – při volání `Open`, přepsání výchozího příkazu SQL sady záznamů. Další informace naleznete v tématu [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) v *knihovně tříd reference* a [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) a [sady záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Efektivně provádět mnoho dotazů s různými informacemi o parametrech.

   Například pokaždé, když koncový uživatel vyhledává informace pro konkrétního studenta v registrační databázi studenta, můžete zadat jméno nebo ID studenta jako parametr získaný od uživatele. Pak při volání členské funkce `Requery` sady záznamů, dotaz vybere pouze záznam studenta.

   Řetězec filtru vaší sady záznamů, uložený v `m_strFilter`, může vypadat takto:

    ```cpp
    "StudentID = ?"
    ```

   Předpokládejme, že získáte ID studenta v proměnné `strInputID`. Když nastavíte parametr na `strInputID` (například student ID 100), hodnota proměnné je svázána se zástupným symbolem parametru reprezentovaným znakem "?" v řetězci filtru.

   Přiřaďte hodnotu parametru následujícím způsobem:

    ```cpp
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   Nechcete nastavit řetězec filtru tímto způsobem:

    ```cpp
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Diskuzi o tom, jak správně používat uvozovky pro filtrační řetězce, naleznete v tématu [Sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

   Hodnota parametru se liší pokaždé, když znovu spustíte dotaz na sadu záznamů pro nové ID studenta.

   > [!TIP]
   > Použití parametru je efektivnější než jen filtr. Pro parametrizovanou sadu záznamů musí databáze zpracovat příkaz SQL **Select** pouze jednou. Pro filtrovanou sadu záznamů bez parametrů je nutné zpracovat příkaz **Select** pokaždé, když `Requery` s novou hodnotou filtru.

Další informace o filtrech naleznete v tématu [Sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

##  <a name="parameterizing-your-recordset-class"></a><a name="_core_parameterizing_your_recordset_class"></a>Parametrizace vaší třídy sady záznamů

> [!NOTE]
> Tato část se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, implementace parametrů je podobný proces. Další informace naleznete v tématu [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Před vytvořením třídy sady záznamů určete, jaké parametry potřebujete, jaké jsou jejich datové typy a jak je sada záznamů používá.

#### <a name="to-parameterize-a-recordset-class"></a>Parametrizovat třídu sady záznamů

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Tuto funkci můžete přesto vytvořit ručně.

1. Spusťte [Průvodce příjemcem knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Přidat třídu** pro vytvoření třídy.

1. Zadejte datové členy pole pro sloupce sady záznamů.

1. Poté, co průvodce zapíše třídu do souboru v projektu, přejít na soubor. h a ručně přidat jeden nebo více datových členů parametrů do deklarace třídy. Sčítání může vypadat podobně jako v následujícím příkladu, což je část třídy snímku navržená tak, aby odpovídala dotazu "které studenti jsou ve třídě zkušení?"

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

   Přidejte datové členy parametru za datové členy pole generované průvodcem. Konvence má připojit slovo "param" ke každému uživatelsky definovanému názvu parametru.

1. Upravte definici členské funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) v souboru. cpp. Přidejte volání funkce RFX pro každý datový člen parametru, který jste přidali do třídy. Informace o psaní funkcí RFX naleznete v tématu [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Předchází volání RFX pro parametry s jedním voláním:

    ```cpp
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. V konstruktoru třídy sady záznamů zvyšte počet parametrů `m_nParams`.

   Informace najdete v tématu [Výměna polí záznamu: práce s kódem průvodce](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Při psaní kódu, který vytvoří objekt sady záznamů této třídy, umístěte znak "?". (otazník) symbol na každém místě řetězce příkazu SQL, kde má být parametr nahrazen.

   V době běhu jsou zástupné symboly "?" vyplněny v pořadí podle hodnot parametrů, které předáte. První parametr datový člen nastavený po volání [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) nahrazuje první znak "?" v řetězci SQL, druhý datový člen s parametrem nahradí druhý "?" atd.

> [!NOTE]
> Pořadí parametrů je důležité: pořadí volání RFX pro parametry ve vaší funkci `DoFieldExchange` musí odpovídat pořadí zástupných symbolů parametrů v řetězci SQL.

> [!TIP]
> Nejpravděpodobnější řetězec pro práci s je řetězec, který zadáte (pokud existuje) pro datový člen [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) třídy, ale některé ovladače rozhraní ODBC mohou v jiných klauzulích SQL umožňovat parametry.

##  <a name="passing-parameter-values-at-run-time"></a><a name="_core_passing_parameter_values_at_run_time"></a>Předávání hodnot parametrů za běhu

Je nutné zadat hodnoty parametrů před voláním `Open` (pro nový objekt recordset) nebo `Requery` (pro existující objekt sady záznamů).

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Předání hodnot parametrů do objektu Recordset v době běhu

1. Sestavte objekt sady záznamů.

1. Připravte řetězec nebo řetězce, jako je například řetězec `m_strFilter`, obsahující příkazy SQL nebo jejich části. Vložte zástupné symboly "?", kde se informace o parametrech přecházejí.

1. Přiřaďte hodnotu parametru run-time každému datovému členu parametru objektu.

1. Zavolejte členskou funkci `Open` (nebo `Requery`pro existující sadu záznamů).

Předpokládejme například, že chcete zadat řetězec filtru pro sadu záznamů pomocí informací získaných v době běhu. Předpokládejme, že jste vytvořili sadu záznamů třídy `CStudentSet` dříve – označované jako `rsStudents` – a teď se chcete znovu dotazovat na konkrétní druh informací studenta.

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

Sada záznamů obsahuje záznamy pro studenty, jejichž záznamy splňují podmínky určené filtrem, který byl vytvořen z běhových parametrů. V tomto případě sada záznamů obsahuje záznamy pro všechny vyšší studenty.

> [!NOTE]
>  V případě potřeby můžete nastavit hodnotu datového členu parametru na hodnotu null pomocí [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Můžete také ověřit, zda je datový člen parametru null, pomocí [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)