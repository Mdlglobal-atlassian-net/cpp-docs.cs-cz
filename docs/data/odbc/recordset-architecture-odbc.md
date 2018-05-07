---
title: 'Sada záznamů: Architektura (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5be3ec16ec01a6c6db2e24b1b6a6260f3a44bfec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-architecture-odbc"></a>Sada záznamů: Architektura (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma popisuje datových členů, které tvoří architektura objektu sady záznamů:  
  
-   [Pole datových členů](#_core_field_data_members)  
  
-   [Parametry datových členů](#_core_parameter_data_members)  
  
-   [Pomocí m_nFields a m_nParams datové členy](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud se implementuje hromadné načítání řádků, je podobný architekturu. Chcete-li pochopit rozdíly, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_a_sample_class"></a> Ukázkový – třída  
 Při použití [průvodce příjemcem knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **přidat třídu** Průvodce deklarovat třídu sady záznamů odvozené z `CRecordset`, výsledná třída má obecnou strukturu vidět v následujícím jednoduché Třída:  
  
```  
class CCourse : public CRecordset  
{  
public:  
   CCourse(CDatabase* pDatabase = NULL);  
   ...  
   CString m_strCourseID;  
   CString m_strCourseTitle;  
   CString m_strIDParam;  
};  
```  
  
 Na začátku třídy, průvodce zapíše sadu [pole datových členů](#_core_field_data_members). Když vytváříte třídu, musíte zadat jeden nebo více pole datových členů. Pokud je třída parametrizovaná, jako v ukázkovém třída je (s datový člen `m_strIDParam`), je třeba ručně přidat [parametry datových členů](#_core_parameter_data_members). Průvodce nepodporuje přidávání parametrů do třídy.  
  
##  <a name="_core_field_data_members"></a> Pole datových členů  
 Nejdůležitější členy vaší třídy sady záznamů jsou pole datových členů. Pro každý sloupec, který je vybrán ze zdroje dat obsahuje třídu členem dat odpovídající datový typ daného sloupce. Například [ukázkové třídy](#_core_a_sample_class) zobrazí na začátku tohoto tématu má dvě pole datových členů, obě typu `CString`, názvem `m_strCourseID` a `m_strCourseTitle`.  
  
 Pokud sada záznamů vybere sadu záznamů, systém automaticky naváže sloupce záznam na aktuální záznam (po **otevřete** volání na první záznam je aktuální) do pole datových členů objektu. To znamená systém použije příslušná pole datového člena jako vyrovnávací paměť pro uložení obsahu sloupce záznam.  
  
 Jako uživatel posune na nový záznam, používá rozhraní pole datových členů k reprezentaci aktuální záznam. Systém aktualizuje pole datových členů, nahraďte hodnoty předchozího záznamu. Pole datových členů se také používají pro aktualizaci aktuálního záznamu a pro přidání nové záznamy. Jako součást procesu aktualizace záznamu zadejte hodnoty aktualizace přiřazením hodnoty přímo do příslušného pole datového člena nebo členy.  
  
##  <a name="_core_parameter_data_members"></a> Parametry datových členů  
 Pokud je třída parametrizovaná, má jeden nebo více parametry datových členů. Parametrizované třída umožňuje základní sada záznamů dotazu na informace o získaných nebo vypočtených za běhu.  
  
 Parametr obvykle pomáhá zúžení výběru, jako v následujícím příkladu. Na základě [ukázkové třídy](#_core_a_sample_class) na začátku tohoto tématu, může objekt záznamů spustit následující příkaz SQL:  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 "?" Je zástupný symbol pro hodnotu parametru, který zadáte v době běhu. Když vytvoříte sadu záznamů a nastavit jeho `m_strIDParam` na MATH101 – datový člen, bude efektivní příkazu SQL sady záznamů:  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 Definováním parametry datových členů informujete systém o parametrech v řetězci SQL. Rozhraní framework sváže parametr, který umožňuje, aby věděli, kde získat hodnoty pro nahrazení zástupného textu ODBC. V příkladu Výsledná sada záznamů obsahuje pouze záznam z kurzu tabulky se sloupcem CourseID, jehož hodnota je MATH101. Jsou vybrány všechny zadané sloupce tento záznam. Můžete zadat libovolný počet parametrů (a zástupné symboly) podle potřeby.  
  
> [!NOTE]
>  MFC neprovede žádnou akci, samotné s parametry – konkrétně neprovede nahrazování textu. Místo toho MFC udává ODBC, kde získat parametr; Rozhraní ODBC data načte a provede nezbytné parametrizace.  
  
> [!NOTE]
>  Je důležité pořadí parametrů. Informace o této a další informace o parametrech najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> Použití m_nFields a m_nParams  

 Když průvodce zapíše konstruktor pro třídu, také inicializuje [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) datového člena, který určuje počet [pole datových členů](#_core_field_data_members) ve třídě. Pokud přidáte některé [parametry](#_core_parameter_data_members) na třídu, musíte taky přidat inicializaci pro [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) datového člena, který určuje počet parametry datových členů. Rozhraní používá tyto hodnoty pro práci s datových členů.  
  
 Další informace a příklady naleznete v tématu [výměna polí záznamu: Použití RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)