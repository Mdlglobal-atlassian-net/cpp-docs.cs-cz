---
title: "CAccessorRowset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
dev_langs: C++
helpviewer_keywords: CAccessorRowset class
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9750393a96a504b20ce861624ba94f8336fd9d4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="caccessorrowset-class"></a>CAccessorRowset – třída
Zapouzdří sadu řádků a její přidružené přístupové objekty do jedné třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <   
   class TAccessor = CNoAccessor,    
   template <typename T> class TRowset = CRowset    
>  
class CAccessorRowset :   
   public TAccessor,    
   public TRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Třídu přistupujícího objektu.  
  
 `TRowset`  
 Třídy sady řádků.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Vazby](../../data/oledb/caccessorrowset-bind.md)|Vytvoří vazbu (použít, když **bBind** je zadán jako false v [CCommand::Open](../../data/oledb/ccommand-open.md)).|  
|[CAccessorRowset](../../data/oledb/caccessorrowset-caccessorrowset.md)|Konstruktor|  
|[Zavřete](../../data/oledb/caccessorrowset-close.md)|Zavře sadu řádků a všechny přistupující objekty.|  
|[Freerecordmemory –](../../data/oledb/caccessorrowset-freerecordmemory.md)|Uvolní všechny sloupce v aktuální záznam, který musí být uvolněno.|  
|[GetColumnInfo –](../../data/oledb/caccessorrowset-getcolumninfo.md)|Implementuje [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx).|  
  
## <a name="remarks"></a>Poznámky  
 Třída `TAccessor` spravuje přistupujícího objektu. Třída *TRowset* spravuje sadu řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)