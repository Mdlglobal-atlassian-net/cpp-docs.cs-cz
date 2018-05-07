---
title: SCHEMA_ENTRY | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- SCHEMA_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- SCHEMA_ENTRY macro
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 665b337861959b28670a0b2e57649814853a7384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="schemaentry"></a>SCHEMA_ENTRY
Přiřadí identifikátor GUID s třídou.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 Sadu řádků schématu identifikátor GUID. V tématu [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v *referenční příručka programátora technologie OLE DB* seznam sad řádků schématu a jejich identifikátory GUID.  
  
 *rowsetClass*  
 Třída, která se vytvoří představující sadu řádků schématu.  
  
## <a name="remarks"></a>Poznámky  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) pak můžete dotazu mapy pro seznamu identifikátorů GUID, nebo ji můžete vytvořit sadu řádků, pokud je vydáno identifikátor GUID. Sada řádků schématu `IDBSchemaRowsetImpl` vytvoří je podobná standard `CRowsetImpl`-odvozené třídy, s výjimkou musíte zadat **Execute** metoda, která má následující podpis:  
  
```  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 To **Execute** funkce naplní datové sady řádků. Průvodce projektem ATL vytvoří, jak je popsáno v [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v *referenční příručka programátora technologie OLE DB*, tři počáteční sad řádků schématu v projektu pro všechny tři povinné OLE DB schémat:  
  
-   `DBSCHEMA_TABLES`  
  
-   **DBSCHEMA_COLUMNS**  
  
-   **DBSCHEMA_PROVIDER_TYPES**  
  
 Průvodce také přidá tři odpovídající položky v tomto schématu mapování. V tématu [vytvoření poskytovatele šablony technologie OLE DB](../../data/oledb/creating-an-ole-db-provider.md) Další informace o používání Průvodce při vytváření zprostředkovatele.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)