---
title: IDBInitializeImpl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBInitializeImpl class
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4e18d220b8ca7da0e76ac1434cebf851ef40ad67
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105735"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl – třída
Poskytuje implementaci pro [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IDBInitializeImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Idbinitializeimpl –](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)|Konstruktor|  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[Initialize](../../data/oledb/idbinitializeimpl-initialize.md)|Spustí zprostředkovatele.|  
|[Uninitialize –](../../data/oledb/idbinitializeimpl-uninitialize.md)|Zastaví zprostředkovatele.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_dwStatus](../../data/oledb/idbinitializeimpl-m-dwstatus.md)|Zdroje dat příznaky.|  
|[m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)|Ukazatel na implementaci DB vlastnosti informací.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní na objekty zdroje dat a volitelné rozhraní na výčty.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)