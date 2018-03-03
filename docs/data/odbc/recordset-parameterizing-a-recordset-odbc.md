---
title: "Sada záznamů: Parametrizace sady záznamů (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- parameterizing recordsets
- ODBC recordsets, parameterizing
- recordsets, parameterizing
- passing parameters, to queries at runtime
ms.assetid: 7d1dfeb6-5ee0-45e2-aacc-63bc52a465cd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 38b17950a7aaf89cc041c4933768bf6b2da0c9b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-parameterizing-a-recordset-odbc"></a>Sada záznamů: Parametrizace sady záznamů (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 V některých případech můžete chtít bude moci vybrat záznamy v době běhu pomocí informací o jste vypočítali nebo získali od vašeho koncového uživatele. Sada záznamů parametry umožňují dosažení tohoto cíle.  
  
 Toto téma vysvětluje:  
  
-   [Účel parametrizované sady záznamů](#_core_parameterized_recordsets).  
  
-   [Kdy a proč můžete chtít Parametrizace sady záznamů](#_core_when_to_use_parameters).  
  
-   [Jak deklarovat parametr datových členů v třídu sady záznamů](#_core_parameterizing_your_recordset_class).  
  
-   [Jak předat informace o parametrech objekt sady záznamů v době běhu](#_core_passing_parameter_values_at_run_time).  
  
##  <a name="_core_parameterized_recordsets"></a>Parametrizované sady záznamů  
 Parametrizované sady záznamů umožňuje předat informace o parametrech v době běhu. To má dva důležité efekty:  
  
-   Výsledkem může být vyšší rychlost provádění.  
  
-   Umožňuje vytvoření dotazu v době běhu na základě informací není k dispozici v době návrhu, například informace získané z vašeho uživatele nebo vypočtených za běhu.  
  
 Při volání **otevřete** spusťte dotaz, používá sada záznamů informace o parametrech k dokončení jeho **SQL SELECT** příkaz. Můžete parametrizovat všechny sady záznamů.  
  
##  <a name="_core_when_to_use_parameters"></a>Pokud chcete používat parametry  
 Typické použití parametrů patří:  
  
-   Předání argumentů běhu pro předdefinovaný dotaz.  
  
     Předat parametry do uložené procedury, je nutné zadat úplný vlastní ODBC **volání** příkaz – se zástupnými symboly parametru – při volání **otevřete**, přepsání příkazu SQL sady záznamů výchozí. Další informace najdete v tématu [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) v *knihovny tříd* a [SQL: přizpůsobení vaše SQL příkazu záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md) a [ Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  

  
-   Efektivní provádění mnoha opakovaných dotazů s jiným parametrem informace.  
  
     Například pokaždé, když koncový uživatel vyhledává informace pro konkrétní student v databázi registrací studentů, můžete název nebo ID Studentova jako parametr získaný od uživatele. Potom při volání sady záznamů **Requery –** – členská funkce dotaz vybere pouze tento Studentova záznam.  
  
     Řetězec filtru sady záznamů, které jsou uložené v **m_strFilter**, může vypadat například takto:  
  
    ```  
    "StudentID = ?"  
    ```  
  
     Předpokládejme, že obdržíte ID student v proměnné `strInputID`. Pokud nastavíte parametr na `strInputID` (například studenty ID 100) hodnotu proměnné je vázána na parametr zástupný symbol reprezentována "?" v řetězci filtru.  
  
     Hodnota parametru přiřadíte takto:  
  
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
  
     Informace o tom, jak použití uvozovek v řetězcích filtrů, naleznete v [sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
     Hodnota parametru je pokaždé jiný Requery – sady záznamů pro nové ID student.  
  
    > [!TIP]
    >  Použití parametru je efektivnější než jednoduše filtru. Pro parametrizované sady záznamů, musí databáze zpracovat SQL **vyberte** příkaz pouze jednou. Pro filtrovanou sadu záznamů bez parametrů **vyberte** musí být příkaz zpracován pokaždé, když provedete **Requery** s novou hodnotou filtru.  
  
 Další informace o filtrech najdete v tématu [sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).  
  
##  <a name="_core_parameterizing_your_recordset_class"></a>Parametrizace vaší třídy sady záznamů  
  
> [!NOTE]
>  Tato část se týká objektů odvozených od `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, implementace parametrů je podobný proces. Další informace najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Než vytvoříte třídu sady záznamů, určete, jaké parametry, je nutné, jaké jsou jejich datové typy a jak je sada záznamů použije.  
  
#### <a name="to-parameterize-a-recordset-class"></a>O parametrizaci třídy sady záznamů  
  
1.  Spustit [průvodce příjemcem knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **přidat třídu** třídu vytvořte.  
  
2.  Zadejte pole datových členů pro sloupce sady záznamů.  
  
3.  Poté, co průvodce zapíše třídu do souboru ve vašem projektu, přejděte do souboru h a ručně přidat jeden nebo více parametry datových členů do deklaraci třídy. Přidání může vypadat podobně jako v následujícím příkladu, součástí třídy snímku navržený tak, aby odpovědět dotaz "které studenti, kteří jsou ve třídě pokročilých?"  
  
    ```  
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
  
     Přidání členů parametr dat po generované v Průvodci pole datových členů. Konvence je slovo "Param" připojit k název každého parametru definovaný uživatelem.  
  
4.  Změnit [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) definice členské funkce v souboru. Přidejte volání funkce RFX pro každý parametr datového člena, které jste přidali do třídy. Informace o psaní vašich funkcí RFX najdete v tématu [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Předcházejte volání RFX pro parametry pomocí jednoho volání:  
  
    ```  
    pFX->SetFieldType( CFieldExchange::param );  
    // RFX calls for parameter data members  
    ```  
  
5.  V konstruktoru vaší třídy sady záznamů, zvyšte počet parametrů, `m_nParams`.  
  
     Informace najdete v tématu [výměna polí záznamu: práce s kódem průvodce](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md).  
  
6.  Při psaní kódu, který vytvoří objekt sady záznamů této třídy, umístěte "?" symbol (otazník) v každé místo vašich řetězců příkazů SQL, kde parametr má být nahrazen.  
  
     V době běhu "?" zástupné symboly jsou vyplněny v pořadí, podle hodnoty parametru předáte. První parametr datového člena nastavit po [SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) volání nahradí první "?"v řetězci SQL, druhý parametr datového člena nahradí druhý"?", a tak dále.  
  
> [!NOTE]
>  Parametr pořadí je důležité: pořadí RFX volání pro parametry v vaší `DoFieldExchange` funkce musí odpovídat pořadí zástupných symbolů parametrů ve vašem řetězci SQL.  
  
> [!TIP]

>  Pro práci s největší pravděpodobností řetězec je řetězec zadáte (pokud existuje) pro zadanou třídu [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) – datový člen, ale některé ovladače ODBC mohou povolit parametry v jiných klauzulích SQL.  
  
##  <a name="_core_passing_parameter_values_at_run_time"></a>Předávání hodnot parametrů v době běhu  
 Musíte zadat hodnoty parametrů před voláním **otevřete** (pro nový objekt sady záznamů) nebo **Requery –** (pro již existující).  
  
#### <a name="to-pass-parameter-values-to-a-recordset-object-at-run-time"></a>Chcete-li předat hodnoty parametrů objektu sady záznamů v době běhu  
  
1.  Vytvořte objekt sady záznamů.  
  
2.  Příprava řetězec nebo řetězce, například **m_strFilter** řetězec, obsahující příkazu SQL, nebo její části. Uveďte "?" zástupné symboly, kde je informace o parametru přejít.  
  
3.  Hodnota parametru runtime přiřadíte každý parametr datového člena objektu.  
  
4.  Volání **otevřete** – členská funkce (nebo **Requery –**, pro existující sady záznamů).  
  
 Předpokládejme například, že chcete zadejte řetězec filtru pro sady záznamů pomocí informací získaných v době běhu. Předpokládejme, kterou jste vytvořili sadu záznamů třídy `CStudentSet` dříve – názvem `rsStudents` – a teď chcete znovu spustit dotaz pro konkrétní typ student informace.  
  
```  
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
  
 Sada záznamů obsahuje záznamy pro tyto studenty, jejichž záznamy splňovat podmínky zadaný filtr, který byl vytvořen z parametrů běhu. V takovém případě sada záznamů obsahuje záznamy všech pokročilých studentů.  
  
> [!NOTE]
>  V případě potřeby můžete nastavit hodnotu datového členu parametru na hodnotu Null, pomocí [SetParamNull](../../mfc/reference/crecordset-class.md#setparamnull). Podobně můžete zkontrolovat, zda je parametr datového člena Null pomocí [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)