---
title: "Třídy generované v Průvodci příjemcem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- command classes in OLE DB consumer
- classes [C++], OLE DB Consumer Wizard-generated
- consumer wizard-generated classes and methods
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ebd53b8b39fb94e4275f5052a74f77bf71bd790
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="consumer-wizard-generated-classes"></a>Třídy generované v průvodci příjemcem
Pokud použijete průvodce příjemcem knihovny ATL technologie OLE DB pro vygenerování příjemce, máte možnost použití šablony technologie OLE DB nebo OLE DB atributů. V obou případech vygeneruje průvodce příkaz třídy a třídy uživatelského záznamu. Příkaz třída obsahuje kód pro otevření zdroje dat a sady řádků, které zadáte v průvodci. Třída záznamu uživatele obsahuje mapu sloupce pro tabulku databáze, kterou jste vybrali. Generovaný kód se ale liší v každém případě:  
  
-   Pokud vyberete podle šablony příjemce, průvodce vygeneruje třídu příkazu a třídu záznamu uživatele. Třída příkazu bude mít název, který zadáte do pole – Třída v průvodci (například `CProducts`), a třída uživatelského záznamu bude mít název ve tvaru "*ClassName*přistupujícího objektu" (například `CProductsAccessor`). Obě třídy jsou umístěny v záhlaví souboru příjemce.  
  
-   Pokud vyberete s atributy příjemce, třída uživatelského záznamu bude mít název ve tvaru "_*ClassName*přistupujícího objektu" a budou vloženy. To znamená nebudete moci zobrazit pouze třídu příkazu v textovém editoru; třídy uživatelského záznamu můžete zobrazit jenom jako vloženého kódu. Informace o zobrazení vloženého kódu najdete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).  
  
 Následující příklady použít třídu příkazu vytvořit v tabulce produkty databáze Northwind k předvedení kód vygenerované průvodcem příjemce pro třídu příkazu a třída záznamu uživatele.  
  
## <a name="templated-user-record-classes"></a>Třídy záznam šablonované uživatelů  
 Pokud vytvoříte příjemce technologie OLE DB pomocí šablony technologie OLE DB (nikoli atributy technologie OLE DB), Průvodce generuje kód, jak je popsáno v této části.  
  
### <a name="column-data-members"></a>Sloupec datové členy  
 První část třída záznamu uživatele obsahuje deklarace členů dat a stavu a délky datových členů pro každý sloupec vázané na data. Informace o těchto datových členů, najdete v tématu [Datoví členové stavu pole v přístupových objektech generovaných průvodcem](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
> [!NOTE]
>  Pokud změníte třídu záznamu uživatele nebo napsat vlastní příjemce, data proměnné musí předcházet proměnné stavu a délka.  
  
> [!NOTE]
>  Průvodce příjemcem knihovny ATL technologie OLE DB používá **DB_NUMERIC** typ pro vazbu číselné datové typy. Dříve používanou **DBTYPE_VARNUMERIC** (formát, který je popsán **DB_VARNUMERIC** typ; viz Oledb.h). Pokud použijete průvodce k vytvoření příjemce, doporučuje se použít **DB_NUMERIC**.  
  
```  
// Products.H : Declaration of the CProducts class  
  
class CProductsAccessor  
{  
public:  
   // Column data members:  
   LONG m_ProductID;  
   TCHAR m_ProductName[41];  
   LONG m_SupplierID;  
   LONG m_CategoryID;  
   TCHAR m_QuantityPerUnit[21];  
   CURRENCY m_UnitPrice;  
   SHORT m_UnitsInStock;  
   SHORT m_UnitsOnOrder;  
   SHORT m_ReorderLevel;  
   VARIANT_BOOL m_Discontinued;  
  
   // Column status data members:  
   DBSTATUS m_dwProductIDStatus;  
   DBSTATUS m_dwProductNameStatus;  
   DBSTATUS m_dwSupplierIDStatus;  
   DBSTATUS m_dwCategoryIDStatus;  
   DBSTATUS m_dwQuantityPerUnitStatus;  
   DBSTATUS m_dwUnitPriceStatus;  
   DBSTATUS m_dwUnitsInStockStatus;  
   DBSTATUS m_dwUnitsOnOrderStatus;  
   DBSTATUS m_dwReorderLevelStatus;  
   DBSTATUS m_dwDiscontinuedStatus;  
  
   // Column length data members:  
   DBLENGTH m_dwProductIDLength;  
   DBLENGTH m_dwProductNameLength;  
   DBLENGTH m_dwSupplierIDLength;  
   DBLENGTH m_dwCategoryIDLength;  
   DBLENGTH m_dwQuantityPerUnitLength;  
   DBLENGTH m_dwUnitPriceLength;  
   DBLENGTH m_dwUnitsInStockLength;  
   DBLENGTH m_dwUnitsOnOrderLength;  
   DBLENGTH m_dwReorderLevelLength;  
   DBLENGTH m_dwDiscontinuedLength;  
```  
  
### <a name="rowset-properties"></a>Vlastnosti sady řádků  
 V dalším kroku Průvodce nastavuje vlastnosti sady řádků. Pokud jste vybrali **změnu**, **vložit**, nebo **odstranit** v Průvodci příjemce knihovny ATL technologie OLE DB odpovídající vlastnosti nastaveny zde (DBPROP_IRowsetChange je vždy nastavena, pak jeden nebo více DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT a/nebo DBPROPVAL_UP_DELETE, v uvedeném pořadí).  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
### <a name="command-or-table-class"></a>Příkaz nebo tabulky – třída  
 Pokud zadáte příkaz třídy, Průvodce deklaruje třídu příkazu; pro kódu s použitím šablon příkaz vypadat třeba takto:  
  
```  
DEFINE_COMMAND_EX(CProductsAccessor, L" \  
SELECT \  
   ProductID, \  
   ProductName, \  
   SupplierID, \  
   CategoryID, \  
   QuantityPerUnit, \  
   UnitPrice, \  
   UnitsInStock, \  
   UnitsOnOrder, \  
   ReorderLevel, \  
   Discontinued \  
   FROM dbo.Products")  
```  
  
### <a name="column-map"></a>Mapu sloupce  
 Průvodce potom generuje vazeb sloupců nebo mapu sloupce. Pokud chcete vyřešit několik problémů s někteří poskytovatelé, následující kód vázat sloupce v jiném pořadí než hlášené zprostředkovatele.  
  
```  
   BEGIN_COLUMN_MAP(CProductsAccessor)  
      COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(3, m_SupplierID, m_dwSupplierIDLength, m_dwSupplierIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(4, m_CategoryID, m_dwCategoryIDLength, m_dwCategoryIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(5, m_QuantityPerUnit, m_dwQuantityPerUnitLength, m_dwQuantityPerUnitStatus)  
      _COLUMN_ENTRY_CODE(6, DBTYPE_CY, _SIZE_TYPE(m_UnitPrice), 0, 0, offsetbuf(m_UnitPrice), offsetbuf(m_dwUnitPriceLength), offsetbuf(m_dwUnitPriceStatus))  
      COLUMN_ENTRY_LENGTH_STATUS(7, m_UnitsInStock, m_dwUnitsInStockLength, m_dwUnitsInStockStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(8, m_UnitsOnOrder, m_dwUnitsOnOrderLength, m_dwUnitsOnOrderStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(9, m_ReorderLevel, m_dwReorderLevelLength, m_dwReorderLevelStatus)  
      _COLUMN_ENTRY_CODE(10, DBTYPE_BOOL, _SIZE_TYPE(m_Discontinued), 0, 0, offsetbuf(m_Discontinued), offsetbuf(m_dwDiscontinuedLength), offsetbuf(m_dwDiscontinuedStatus))  
   END_COLUMN_MAP()  
};  
```  
  
### <a name="class-declaration"></a>Deklarace třídy  
 Nakonec průvodce vygeneruje deklaraci třídy příkazu například následující:  
  
```  
class CProducts : public CCommand<CAccessor<CProductsAccessor> >  
```  
  
## <a name="attribute-injected-user-record-classes"></a>Třídy atributově uživatelských záznamů  
 Pokud vytvoříte příjemce technologie OLE DB pomocí atributů databáze ([db_command](../../windows/db-command.md) nebo [db_table](../../windows/db-table.md)), vloží atributy třídy uživatelského záznamu s jméno ve tvaru "_*ClassName*Přistupujícího objektu. " Například, pokud jste s názvem třídě příkaz `COrders`, třída uživatelského záznamu bude `_COrdersAccessor`. Přestože třída uživatelského záznamu se zobrazí v zobrazení tříd, dvojitým kliknutím k třídě příkazu nebo tabulky v záhlaví souboru místo toho. V těchto případech můžete zobrazit pouze skutečné deklaraci třídy uživatelského záznamu zobrazením kód atributově.  
  
 Může být potenciální komplikace Pokud přidáte nebo přepsání metody s atributy uživatele. Například můžete přidat `_COrdersAccessor` konstruktor `COrders` deklarace, ale Všimněte si, že to ve skutečnosti přidá konstruktor do vložené `COrdersAccessor` třídy. Takový konstruktor může inicializovat sloupce/parametry, ale nelze vytvořit kopírovacího konstruktoru tímto způsobem, protože nemůže přímo `COrdersAccessor` objektu. Pokud potřebujete konstruktoru (nebo jiné metody) přímo na `COrders` třídy, se doporučuje definovat novou třídu odvozování z `COrders` a přidejte nezbytné metody.  
  
 V následujícím příkladu, vygeneruje průvodce deklaraci pro třídu `COrders`, ale třída uživatelského záznamu `COrdersAccessor` nezobrazí, protože vloží atributy.  
  
```  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
[  
   db_source(L"your connection string"),  
   db_command(L"Select ShipName from Orders;")  
]  
class COrders  
{  
public:  
  
   // COrders()            // incorrect constructor name  
   _COrdersAccessor()      // correct constructor name  
   {  
   }  
      [db_column(1) ] TCHAR m_ShipName[41];  
   };  
```  
  
 Deklarace třídy vloženého příkaz vypadá takto:  
  
```  
class CProducts : public CCommand<CAccessor<_CProductsAccessor> >  
```  
  
 Většina vloženého kódu je stejný jako nebo podobné na základě šablony verzi. Hlavní rozdíly jsou v vloženého metody, které jsou popsané v [vygenerované metody](../../data/oledb/consumer-wizard-generated-methods.md).  
  
 Informace o zobrazení vloženého kódu najdete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)