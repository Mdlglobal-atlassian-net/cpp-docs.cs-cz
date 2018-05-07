---
title: IRowsetCreatorImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0492994193130ffa6a547691490b4da1ae557c8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl – třída
Provádí stejné funkce jako `IObjectWithSite` , ale taky umožňuje vlastnosti OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída odvozená z **IRowsetCreator**.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Setsite –](../../data/oledb/irowsetcreatorimpl-setsite.md)|Nastaví lokality, která obsahuje objekt sady řádků.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída dědí z [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) a přepíše [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). Objekt zprostředkovatele příkaz nebo relace vytvoří sadu řádků, zavolá `QueryInterface` na objektu sady řádků hledá `IObjectWithSite` a volání `SetSite` předání objektu sady řádků **IUnkown** rozhraní jako rozhraní lokality.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)