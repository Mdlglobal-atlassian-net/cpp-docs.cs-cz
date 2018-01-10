---
title: "IDBSchemaRowsetImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDBSchemaRowsetImpl
dev_langs: C++
helpviewer_keywords: IDBSchemaRowsetImpl class
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b4f451fa408f2f6470281206e5de3670d069b6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl – třída
Poskytuje implementaci pro sady řádků schématu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class SessionClass>  
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `SessionClass`  
 Třída, podle kterého `IDBSchemaRowsetImpl` dědí. Obvykle tuto třídu bude třída relace uživatele.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CheckRestrictions –](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)|Ověří platnost omezení proti sada řádků schématu.|  
|[CreateSchemaRowset –](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)|Implementuje funkce tvůrce objektu COM pro daný objekt zadaný parametrem šablony.|  
|[SetRestrictions –](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)|Určuje, která omezení podpory pro sadu řádků schématu konkrétní.|  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetRowset –](../../data/oledb/idbschemarowsetimpl-getrowset.md)|Vrací sadu řádků schématu.|  
|[GetSchemas –](../../data/oledb/idbschemarowsetimpl-getschemas.md)|Vrátí seznam sad řádků schématu přístupný [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída implementuje [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) rozhraní a funkce šablonou creator [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).  
  
 OLE DB pomocí sad řádků schématu vrátí data o data v zprostředkovatele. Taková data se často říká "metadata." Ve výchozím nastavení, musí zprostředkovatel vždycky podporovat `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, a **DBSCHEMA_PROVIDER_TYPES**, jak je popsáno v [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v  *Referenční příručka programátora prostředí OLE DB*. Schéma sad řádků, jsou určené v mapě schématu. Informace o položkách mapy schématu najdete v tématu [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).  
  
 OLE DB Provider průvodce, v Průvodci objekt knihovny ATL automaticky generuje kód pro schéma sad řádků ve vašem projektu. (Ve výchozím nastavení podporuje Průvodce povinné schéma sad řádků, výše.) Při vytváření příjemce pomocí Průvodce objekt knihovny ATL používá průvodce k vytvoření vazby správná data zprostředkovatele sady řádků schématu. Pokud vaše schéma sad řádků zajistit správné metadata neimplementují, nebude Průvodce vazbu správná data.  
  
 Informace o tom, jak Podpora sad řádků schématu ve zprostředkovateli najdete v tématu [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md).  
  
 Další informace o sad řádků schématu najdete v tématu [sad řádků schématu](https://msdn.microsoft.com/en-us/library/ms712921.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Členy IDBSchemaRowsetImpl – třída](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [Podpora sad řádků schématu](../../data/oledb/supporting-schema-rowsets.md)