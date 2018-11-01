---
title: 'Sada záznamů: Parametrizace sady záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
ms.openlocfilehash: fdea70f8d87604ca0665baa64c8652c14295a670
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506571"
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Sada záznamů: Parametrizace sady záznamů (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Někdy můžete chtít mít možnost vybrat záznamy v době běhu, pomocí informací o mít počítané nebo získané z koncového uživatele. Sada záznamů parametry umožňují dosažení tohoto cíle.

Toto téma vysvětluje:

- [Účelem parametrizované záznamů](#_core_parameterized_recordsets).

- [Kdy a proč můžete chtít Parametrizace sady záznamů](#_core_when_to_use_parameters).

- [Tom, jak deklarovat parametr datové členy ve své třídě záznamů](#_core_parameterizing_your_recordset_class).

- [Jak předat informace o parametrech objekt sady záznamů v době běhu](#_core_passing_parameter_values_at_run_time).

##  <a name="_core_parameterized_recordsets"></a> Parametry sady záznamů

Parametrizované záznamů umožňuje předat informace o parametrech v době běhu. To má dvě důležité důsledky:

- Výsledkem může být lepší rychlostí provádění.

- To umožňuje sestavení dotazu v době běhu na základě informací není k dispozici v době návrhu, jako jsou informace získané z vaší uživatelské nebo vypočítat v době běhu.

Při volání `Open` sady záznamů a spusťte dotaz, použije informace o parametrech k dokončení jeho **SQL SELECT** příkazu. Všechny sady záznamů můžete parametrizovat.

##  <a name="_core_when_to_use_parameters"></a> Kdy použít parametry

Obvyklá využití pro parametry patří:

- Předávání argumentů za běhu pro předdefinovaný dotaz.

   Pro předání parametrů uložené procedury, je nutné zadat úplnou vlastní ODBC **volání** příkaz – se zástupnými symboly parametru – při volání `Open`, přepisuje výchozí příkaz SQL sady záznamů. Další informace najdete v tématu [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) v *knihovny tříd* a [SQL: SQL příkazu přizpůsobení sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) a [ Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

- Efektivní provádění mnoha opakovaných dotazů s informace o různých parametrech.

   Například pokaždé, když koncový uživatel vyhledá informace o konkrétní studentů v registrační databázi student, určíte název nebo ID studenta jako parametr získaný od uživatele. Potom, voláte sady záznamů `Requery` členskou funkci, dotaz vybere pouze student získal záznam.

   Řetězec filtru sady záznamů, které jsou uložené v `m_strFilter`, může vypadat třeba takto:

    ```
    "StudentID = ?"
    ```

   Předpokládejme, že můžete získat ID studenta v proměnné `strInputID`. Pokud nastavíte parametr na `strInputID` (například ID studenta 100) hodnota proměnné je vázán na zástupný symbol parametr, který je reprezentován "?" v řetězci filtru.

   Hodnota parametru také přiřadíte tímto způsobem:

    ```
    strInputID = "100";
    ...
    m_strParam = strInputID;
    ```

   Chcete by se nastavit řetězec filtru tímto způsobem:

    ```
    m_strFilter = "StudentID = 100";   // 100 is incorrectly quoted
                                       // for some drivers
    ```

   Informace o tom, jak správně používat uvozovky řetězce filtru, naleznete v tématu [sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

   Hodnota tohoto parametru je pokaždé jiný requery záznamů pro nové ID studenta.

    > [!TIP]
    >  Pomocí parametru je mnohem efektivnější než jednoduše filtr. Pro parametry sady záznamů, musí zpracovat databázi SQL **vyberte** příkaz pouze jednou. Pro filtrovanou sadu záznamů bez parametrů **vyberte** je potřeba zpracovat příkaz pokaždé, když `Requery` s novou hodnotu filtru.

Další informace o filtrech najdete v tématu [sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).

##  <a name="_core_parameterizing_your_recordset_class"></a> Parametrizace vaší třídy sady záznamů

> [!NOTE]
>  Tato část se týká objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, implementace parametry je podobný proces. Další informace najdete v tématu [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Než vytvoříte třídu sady záznamů, zjistit, jaké parametry se budete potřebovat, jaké jsou jejich datové typy a jak je využívá sadu záznamů.

#### <a name="to-parameterize-a-recordset-class"></a>Chcete-li parametrizovat třídy sady záznamů

1. Spustit [průvodce příjemcem MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **přidat třídu** pro vytvoření třídy.

1. Zadejte pole datových členů pro sady záznamů sloupce.

1. Poté, co průvodce zapíše třídy do souboru ve vašem projektu, přejděte k souboru .h a ručně přidejte jeden nebo více parametry datových členů pro deklaraci třídy. Přidání může vypadat přibližně jako v následujícím příkladu, část třídy snímku navržené tak, aby zodpovědět "které studenty ve třídě vedoucí?"

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

   Přidejte datové členy vašeho parametru po datové členy generované průvodcem pole. Tato konvence je přidat slovo "Parametrů" pro každý název parametru definovaný uživatelem.

1. Upravit [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) definice členské funkce v souboru .cpp. Přidejte volání funkce RFX pro každý parametr datový člen, který jste přidali do třídy. Informace o vytváření funkcí RFX najdete v tématu [výměna polí záznamu: jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md). Předcházejte volání funkce RFX parametrů pomocí jediného volání pro:

    ```
    pFX->SetFieldType( CFieldExchange::param );
    // RFX calls for parameter data members
    ```

1. V konstruktoru třídy sady záznamů, zvyšte počet parametrů `m_nParams`.

   Informace najdete v tématu [výměna polí záznamu: práce s kódem průvodce](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).

1. Když píšete kód, který vytvoří objekt sady záznamů této třídy, umístěte "?" (otazník) v každé místo v řetězci příkaz SQL, kde parametr má být nahrazen.

   V době běhu "?" jsou vyplněny zástupné symboly v pořadí, ve hodnoty parametrů můžete předat. Po první datový člen parametr nastavit [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) volání nahradí první "?"v řetězci SQL, druhý parametr datový člen nahradí druhý"?", a tak dále.

> [!NOTE]
>  Je důležité pořadí parametrů: pořadí RFX volání pro parametry v vaše `DoFieldExchange` funkce musí odpovídat pořadí parametrů zástupné symboly v řetězce jazyka SQL.

> [!TIP]

>  Nejpravděpodobnější řetězec pro práci s je řetězec zadáte (pokud existuje) pro danou třídu [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) datový člen, ale některé ovladače rozhraní ODBC mohou povolit parametry v jiných klauzulích SQL.

##  <a name="_core_passing_parameter_values_at_run_time"></a> Předávání hodnot parametrů v době běhu

Před voláním musíte zadat hodnoty parametrů `Open` (pro nový objekt sady záznamů) nebo `Requery` (pro existující).

#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>K předání hodnot parametru do objektu záznamů v době běhu

1. Vytvořte objekt sady záznamů.

1. Příprava řetězec nebo řetězce, jako `m_strFilter` řetězec, který obsahuje příkaz SQL nebo jeho části. Umístit "?" zástupné symboly, ve kterém je informace o parametrech přejít.

1. Datový člen každý parametr objektu přiřadíte hodnotu parametru za běhu.

1. Volání `Open` členskou funkci (nebo `Requery`, pro existující sady záznamů).

Předpokládejme například, že chcete zadat řetězec filtru pro sady záznamů pomocí informace získané za běhu. Předpokládejme, kterou jste vytvořili sadu záznamů třídy `CStudentSet` dříve – volá `rsStudents` – a teď chcete znovu spustit dotaz pro konkrétní druh informací studentů.

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

Sada záznamů obsahuje záznamy pro tyto studenty, jejichž záznamy splňují podmínky určené filtr, který byl vytvořen z parametrů běhu. V takovém případě sada záznamů obsahuje záznamy pro vedoucí Všichni studenti.

> [!NOTE]
>  V případě potřeby můžete nastavit hodnotu datového členu parametr na hodnotu Null, pomocí [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Podobně můžete zkontrolovat, zda datový člen parametr má hodnotu Null, pomocí [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)