---
title: Třídy generované v Průvodci příjemcem | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/17/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- command classes in OLE DB consumer
- classes [C++], OLE DB Consumer Wizard-generated
- consumer wizard-generated classes and methods
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0473aaae7309f7f041883eea0afab5acc9095c9d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083344"
---
# <a name="consumer-wizard-generated-classes"></a>Třídy generované v průvodci příjemcem

Při použití **průvodce příjemcem ATL OLE DB** generovat příjemce, máte na výběr mezi používáním atributů šablony technologie OLE DB nebo OLE DB. V obou případech průvodce vygeneruje třídu příkazu nebo třída záznamů uživatelů. Třídy příkazů obsahuje kód pro otevření zdroje dat a sady řádků, které jste zadali v průvodci. Třída záznamu uživatele obsahuje mapování sloupců pro tabulku databáze, kterou jste vybrali. Generovaný kód se však liší v každém případě:

- Pokud vyberete příjemce bez vizuálního vzhledu, průvodce vygeneruje třídu příkazu nebo třída záznamů uživatelů. Třídu příkazu bude mít název, který zadáte v **třídy** pole v průvodci (například `CProducts`), a třída záznamů uživatele bude mít název ve tvaru "*ClassName*přístupového objektu" (například) `CProductsAccessor`). Obě třídy jsou umístěny v souboru hlaviček příjemce.

- Pokud vyberete s atributy uživatelů, třída záznamů uživatele bude mít název ve tvaru "_*ClassName*přístupového objektu" a budou vloženy. To znamená budete moci zobrazit pouze třídu příkazu v textovém editoru; Třída záznamů uživatele můžete zobrazit pouze jako vložený kód. Informace o zobrazení vloženého kódu najdete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).

Následující příklady používají vytvořenou na třídu příkazu `Products` tabulku `Northwind` databáze k předvedení generované v Průvodci uživatelský kód pro příkaz třídy a třídy uživatelského záznamu.

## <a name="templated-user-record-classes"></a>Třídy bez vizuálního vzhledu uživatelského záznamu

Pokud vytvoříte příjemce technologie OLE DB pomocí šablony technologie OLE DB (nikoli atributy technologie OLE DB), průvodce vygeneruje kód, jak je popsáno v této části.

### <a name="column-data-members"></a>Sloupce datové členy

První část třída záznamu uživatele obsahuje deklarace členů dat a datové členy stavu a délky pro jednotlivé sloupce vázané na data. Informace o těchto datových členů, najdete v tématu [Datoví členové stavu pole v přístupových objektech generovaných průvodcem](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

> [!NOTE]
> Pokud změníte název třídy záznamu uživatele nebo napsat vlastní příjemce, datových proměnných musí předcházet proměnné stavu a délky.

> [!NOTE]
> Průvodce příjemcem ATL OLE DB používá `DB_NUMERIC` typ vazby číselných datových typů. To dřív používal `DBTYPE_VARNUMERIC` (formát, který je popsán `DB_VARNUMERIC` typ; viz Oledb.h). Pokud použijete průvodce k vytvoření spotřebitelů, doporučuje se, že používáte `DB_NUMERIC`.

```cpp
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

V dalším kroku průvodce nastaví vlastnosti sady řádků. Pokud jste vybrali **změnu**, **vložit**, nebo **odstranit** v Průvodci příjemce knihovny ATL technologie OLE DB příslušných vlastností nastavené, tady (DBPROP_IRowsetChange vždy nastavena, pak jeden nejmíň DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT nebo DBPROPVAL_UP_DELETE, v uvedeném pořadí).

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="command-or-table-class"></a>Příkaz nebo třída tabulky

Pokud chcete zadat třídu příkazu, Průvodce deklaruje třídu příkazu; pro kódu s použitím šablon příkaz vypadá takto:

```cpp
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

### <a name="column-map"></a>Mapování sloupce

Průvodce poté vygeneruje vazeb sloupců nebo mapování sloupců. Chcete-li vyřešit několik výhrad někteří poskytovatelé, následující kód může vytvořit vazbu sloupce v jiném pořadí, než který ohlásil zprostředkovatelem.

```cpp
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

A konečně Průvodce generuje deklaraci třídy příkazu například následující:

```cpp
class CProducts : public CCommand<CAccessor<CProductsAccessor>>
```

## <a name="attribute-injected-user-record-classes"></a>Třídy atributově uživatelských záznamů

Pokud vytvoříte příjemce technologie OLE DB použitím atributů databáze ([db_command](../../windows/db-command.md) nebo [db_table](../../windows/db-table.md)), vloží atributy třídy uživatelského záznamu s názvem ve formátu "_*ClassName*Přistupujícího objektu. " Například pokud pojmenujete vaší třídy příkazu `COrders`, třída záznamů uživatele bude `_COrdersAccessor`. Přestože třída záznamů uživatele se zobrazí v **zobrazení tříd**, dvojitým kliknutím na třídu příkazu nebo tabulky v hlavičkovém souboru místo toho. V těchto případech můžete jenom zobrazit skutečné deklarace třídy uživatelského záznamu zobrazením atributově kódu.

Může existovat možných komplikací Pokud přidáte nebo přepsání metod s atributy uživatelů. Například můžete přidat `_COrdersAccessor` konstruktoru `COrders` deklaraci, ale Všimněte si, že ve skutečnosti to přidá konstruktor do vložené `COrdersAccessor` třídy. Takový konstruktor lze inicializovat sloupce/parametry, ale nelze vytvořit konstruktor kopie tímto způsobem, protože jej nelze doložit přímo `COrdersAccessor` objektu. Pokud potřebujete konstruktoru (nebo jiné metody) přímo na `COrders` třídy, se doporučuje definovat novou třídu odvozenou z `COrders` a přidat nezbytné metody.

V následujícím příkladu, Průvodce generuje deklaraci pro třídu `COrders`, ale třída uživatelského záznamu `COrdersAccessor` nezobrazí, protože vloží atributy.

```cpp
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

```cpp
class CProducts : public CCommand<CAccessor<_CProductsAccessor>>
```

Většina kódu injektovaného je stejná jako nebo podobný bez vizuálního vzhledu verze. Hlavní rozdíly jsou v rámci vloženého metod, které jsou popsány v [vygenerované metody](../../data/oledb/consumer-wizard-generated-methods.md).

Informace o zobrazení vloženého kódu najdete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).

## <a name="see-also"></a>Viz také

[Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)