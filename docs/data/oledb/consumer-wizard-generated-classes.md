---
title: Třídy generované v průvodci příjemcem
ms.date: 05/09/2019
helpviewer_keywords:
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
ms.openlocfilehash: 86da5081fbe63728b062879838ac3ffe78504ccc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211481"
---
# <a name="consumer-wizard-generated-classes"></a>Třídy generované v průvodci příjemcem

::: moniker range="vs-2019"

Průvodce příjemcem OLE DB ATL není v aplikaci Visual Studio 2019 a novějších k dispozici. Tuto funkci můžete přesto přidat ručně.

::: moniker-end

::: moniker range="<=vs-2017"

Když použijete **Průvodce příjemcem OLE DB ATL** k vygenerování příjemce, máte možnost použít šablony OLE DB nebo atributy OLE DB. V obou případech průvodce vygeneruje třídu příkazu a třídu záznamu uživatele. Třída příkazu obsahuje kód pro otevření zdroje dat a sady řádků, které jste zadali v průvodci. Třída záznamu uživatele obsahuje mapu sloupce pro databázovou tabulku, kterou jste vybrali. Vygenerovaný kód se ale v každém případě liší:

- Pokud vyberete uživatele se šablonou, vygeneruje průvodce třídu příkazu a třídu záznamu uživatele. Třída Command bude mít název, který zadáte do pole **Třída** v průvodci (například `CProducts`), a třída záznamu uživatele bude mít název formuláře "*ClassName*přistupující objekt" (například `CProductsAccessor`). Obě třídy jsou umístěny v souboru hlaviček příjemce.

- Pokud vyberete příjemce s atributy, třída záznamu uživatele bude mít název formuláře "_*ClassName*přistupujícího objektu" a bude vložen. To znamená, že v textovém editoru budete moci zobrazit pouze třídu příkazu; můžete zobrazit pouze třídu záznamu uživatele jako vložený kód. Informace o zobrazení vloženého kódu naleznete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).

Následující příklady používají třídu příkazu vytvořenou v `Products` tabulce `Northwind` databáze k předvedení kódu příjemce generovaného průvodcem pro třídu příkazů a třídu záznamu uživatele.

## <a name="templated-user-record-classes"></a>Třídy záznamů uživatelů v šablonách

Pokud vytvoříte příjemce OLE DB pomocí šablon OLE DB (místo atributů OLE DB), průvodce vygeneruje kód, jak je popsáno v této části.

### <a name="column-data-members"></a>Datové členy sloupce

První část třídy záznamu uživatele zahrnuje deklarace datových členů a datové členy stav a délka pro každý sloupec vázaný na data. Informace o těchto datových členech najdete v tématu [datové členy stavu pole v přístupových průvodcích generovaných průvodcem](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

> [!NOTE]
> Pokud upravíte třídu záznamu uživatele nebo zapíšete vlastního příjemce, musí se datové proměnné nacházet před proměnnými stav a délka.

> [!NOTE]
> Průvodce příjemcem OLE DB ATL používá typ `DB_NUMERIC` ke svázání numerických datových typů. Dříve používala `DBTYPE_VARNUMERIC` (formát, který je popsán `DB_VARNUMERIC` typu; viz OLEDB. h). Pokud nepoužíváte průvodce k vytváření uživatelů, doporučujeme použít `DB_NUMERIC`.

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

Dále průvodce nastaví vlastnosti sady řádků. Pokud jste v průvodci OLE DB příjemce knihovny ATL vybrali možnost **změnit**, **Vložit**nebo **Odstranit** , jsou zde nastaveny příslušné vlastnosti (DBPROP_IRowsetChange je vždy nastaveno, pak jedna nebo více DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT a/nebo DBPROPVAL_UP_DELETE v uvedeném pořadí).

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="command-or-table-class"></a>Třída příkazu nebo tabulky

Pokud zadáte třídu příkazu, průvodce deklaruje třídu příkazu; u šablonového kódu bude příkaz vypadat takto:

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

### <a name="column-map"></a>Mapa sloupce

Průvodce pak vygeneruje vazby sloupce nebo mapování sloupce. Chcete-li opravit několik problémů s některými zprostředkovateli, může následující kód navazovat sloupce v jiném pořadí, než je hlášeno zprostředkovatelem.

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

Nakonec průvodce vygeneruje deklaraci třídy příkazu, například následující:

```cpp
class CProducts : public CCommand<CAccessor<CProductsAccessor>>
```

## <a name="attribute-injected-user-record-classes"></a>Třídy záznamů uživatele vložené atributem

Pokud vytvoříte příjemce OLE DB pomocí atributů databáze ([db_command](../../windows/db-command.md) nebo [db_table](../../windows/db-table.md)), atributy vloží třídu záznamu uživatele s názvem formuláře "_*ClassName*přistupujícího objektu". Například pokud jste pojmenovali třídu příkazu `COrders`, třída záznamu uživatele bude `_COrdersAccessor`. I když se třída záznamu uživatele zobrazuje v **zobrazení tříd**, poklikáním přejdete na příkaz nebo třídu tabulky v souboru hlaviček místo toho. V těchto případech můžete zobrazit pouze vlastní deklaraci třídy záznamu uživatele zobrazením kódu vloženého atributem.

Pokud přidáte nebo potlačíte metody v přidaných spotřebitelích, může docházet k potenciálním komplikacím. Například můžete přidat konstruktor `_COrdersAccessor` do deklarace `COrders`, ale Všimněte si, že ve skutečnosti to přidá konstruktor do vložené `COrdersAccessor` třídy. Takový konstruktor může inicializovat sloupce/parametry, ale nelze vytvořit kopírovací konstruktor, protože nemůže přímo vytvořit instanci objektu `COrdersAccessor`. Pokud potřebujete konstruktor (nebo jinou metodu) přímo na `COrders` třídy, doporučujeme, abyste definovali novou třídu odvozenou od `COrders` a tam tam Přidali potřebné metody.

V následujícím příkladu průvodce vygeneruje deklaraci pro třídu `COrders`, ale `COrdersAccessor` třídy záznamu uživatele se nezobrazí, protože atributy je vloží.

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

Deklarace třídy vloženého příkazu vypadá takto:

```cpp
class CProducts : public CCommand<CAccessor<_CProductsAccessor>>
```

Většina vloženého kódu je stejná jako nebo podobná verzi šablony. Hlavní rozdíly jsou ve vložených metodách, které jsou popsány v tématu [metody generované průvodcem příjemce](../../data/oledb/consumer-wizard-generated-methods.md).

Informace o zobrazení vloženého kódu naleznete v tématu [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).

::: moniker-end

## <a name="see-also"></a>Viz také

[Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
