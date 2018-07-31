---
title: 'Sada záznamů: Architektura (ODBC) | Dokumentace Microsoftu'
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
ms.openlocfilehash: 96dfbf9079edefa603a47b73284a4e7fcd8f447c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338103"
---
# <a name="recordset-architecture-odbc"></a>Sada záznamů: Architektura (ODBC)
Toto téma platí pro třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma popisuje datové členy, které tvoří architektura objekt sady záznamů:  
  
-   [Pole datových členů](#_core_field_data_members)  
  
-   [Parametry datových členů](#_core_parameter_data_members)  
  
-   [Pomocí m_nFields a m_nParams datové členy](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud je implementovaná hromadné načítání řádků, se podobá architektuře. Pokud chcete znát rozdíly, přečtěte si téma [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_a_sample_class"></a> Ukázkový – třída  
 Při použití [průvodce příjemcem MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **přidat třídu** průvodce, chcete-li deklarovat třídu sady záznamů odvozený od `CRecordset`, výsledné třídy obsahuje obecnou strukturu je znázorněno v následujícím jednoduché Třída:  
  
```cpp  
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
  
 Na začátek třídy, průvodce zapíše sadu [pole datových členů](#_core_field_data_members). Když vytváříte třídu, je nutné zadat jeden nebo více polí datové členy. Pokud je třída s parametry, jako ukázku třída je (s datový člen `m_strIDParam`), je třeba ručně přidat [parametry datových členů](#_core_parameter_data_members). Průvodce nepodporuje přidávání parametrů do třídy.  
  
##  <a name="_core_field_data_members"></a> Pole datových členů  
 Nejdůležitější členy třídy sady záznamů jsou datové členy polí. Pro každý sloupec, kterou jste vybrali ze zdroje dat obsahuje třídu datový člen třídy odpovídající datový typ pro tento sloupec. Například [ukázková třída](#_core_a_sample_class) uvedené na začátku tohoto tématu má dvě pole datových členů, oba typu `CString`, označované jako `m_strCourseID` a `m_strCourseTitle`.  
  
 Pokud sada záznamů vybere sadu záznamů, systém automaticky sváže sloupce aktuální záznam (po `Open` volání, první záznam je aktuální) na pole datové členy objektu. To znamená, že rozhraní používá datový člen příslušné pole jako vyrovnávací paměť pro uložení obsahu sloupec záznamů.  
  
 Procházení nový záznam rozhraní datové členy polí používá k reprezentaci aktuální záznam. Rozhraní framework aktualizuje pole datových členů, nahraďte hodnoty předchozí záznam. Datové členy polí se používají také k aktualizaci aktuální záznam a pro přidávání nových záznamů. Jako součást procesu aktualizace záznamu zadejte hodnoty aktualizace přiřazením hodnoty přímo do příslušného pole datového člena nebo členy.  
  
##  <a name="_core_parameter_data_members"></a> Parametry datových členů  
 Pokud je třída parametrizovaná, má jeden nebo více parametry datových členů. Parametrizované třída umožňuje základní záznamů dotazu na informace o získaných nebo vypočítat v době běhu.  
  
 Parametr obvykle pomáhá zúžení výběru, jako v následujícím příkladu. Na základě [ukázková třída](#_core_a_sample_class) na začátku tohoto tématu, může být objekt sady záznamů spustit následující příkaz SQL:  
  
```sql  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 "?" Je zástupný symbol pro hodnotu parametru, který zadáte v době běhu. Při vytvoření sady záznamů a nastavte jeho `m_strIDParam` stane datový člen na MATH101 efektivní příkazu SQL sady záznamů:  
  
```sql  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 Definuje parametry datových členů, informování rozhraní framework o parametrech v řetězci SQL. Systém sváže parametr, který umožňuje ODBC věděli, kde získat hodnoty nahraďte zástupný symbol. V příkladu Výsledná sada záznamů obsahuje pouze záznam z kurzu tabulky se sloupcem CourseID, jehož hodnota je MATH101. Jsou vybrané všechny sloupce zadané tohoto záznamu. Můžete zadat libovolný počet parametrů (a zástupné symboly) podle potřeby.  
  
> [!NOTE]
>  Nemá žádný účinek, samotné knihovny MFC s parametry – zejména neprovede nahrazování textu. Místo toho MFC zjistí ODBC, kde získat parametr; ODBC načte data a provede nezbytné parametrizace.  
  
> [!NOTE]
>  Je důležité pořadí parametrů. Informace o této a další informace o parametrech najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> Pomocí m_nFields a m_nParams  

 Když průvodce zapíše konstruktor pro třídu, také inicializuje [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) datového člena, který určuje, kolik [pole datových členů](#_core_field_data_members) ve třídě. Pokud chcete přidat všechny [parametry](#_core_parameter_data_members) do vaší třídy, musíte taky přidat inicializace pro [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) datového člena, který určuje, kolik parametry datových členů. Rozhraní používá tyto hodnoty pro práci s datové členy.  
  
 Další informace a příklady najdete v tématu [výměna polí záznamu: použití funkce RFX](../../data/odbc/record-field-exchange-using-rfx.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)