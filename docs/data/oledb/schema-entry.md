---
title: SCHEMA_ENTRY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SCHEMA_ENTRY
dev_langs: C++
helpviewer_keywords: SCHEMA_ENTRY macro
ms.assetid: e8bee479-80f3-417e-8f41-cdaddd49690c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0919f2ba6474633d98c73cde758dbe6c81549f4f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="schemaentry"></a>SCHEMA_ENTRY
Přiřadí identifikátor GUID s třídou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      SCHEMA_ENTRY(  
   guid,  
   rowsetClass   
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `guid`  
 Sadu řádků schématu identifikátor GUID. V tématu [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v *referenční příručka programátora technologie OLE DB* seznam sad řádků schématu a jejich identifikátory GUID.  
  
 *rowsetClass*  
 Třída, která se vytvoří představující sadu řádků schématu.  
  
## <a name="remarks"></a>Poznámky  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) pak můžete dotazu mapy pro seznamu identifikátorů GUID, nebo ji můžete vytvořit sadu řádků, pokud je vydáno identifikátor GUID. Sada řádků schématu `IDBSchemaRowsetImpl` vytvoří je podobná standard `CRowsetImpl`-odvozené třídy, s výjimkou musíte zadat **Execute** metoda, která má následující podpis:  
  
```  
HRESULT Execute (
    LONG* pcRowsAffected,  
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