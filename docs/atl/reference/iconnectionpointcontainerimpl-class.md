---
title: Třída IConnectionPointContainerImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af5e8b1bc1af0a515cc8fad0500c3f7d040b1eb9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361167"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl – třída
Tato třída implementuje kontejner bod připojení ke správě kolekce [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objekty.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE IConnectionPointContainerImpl 
   : public IConnectionPointContainer
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IConnectionPointContainerImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Vytvoří enumerátor k iteraci v rámci spojovací body podporované v objektu, umožňující připojení.|  
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Načte ukazatele rozhraní k spojovací bod, který podporuje zadaná IID.|  
  
## <a name="remarks"></a>Poznámky  
 `IConnectionPointContainerImpl` implementuje kontejner bod připojení ke správě kolekce [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objekty. `IConnectionPointContainerImpl` nabízí dvě metody, které můžete získat další informace o objekt umožňující připojení volání klienta:  
  
- `EnumConnectionPoints` umožňuje klientovi k určení, které odchozí rozhraní podporuje objektu.  
  
- `FindConnectionPoint` umožňuje klientovi zjistit, zda objekt podporuje určité odchozí rozhraní.  
  
 Informace o používání spojovací body v ATL, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints  
 Vytvoří enumerátor k iteraci v rámci spojovací body podporované v objektu, umožňující připojení.  
  
```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IConnectionPointContainer::EnumConnectionPoints](http://msdn.microsoft.com/library/windows/desktop/ms682460) ve Windows SDK.  
  
##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint  
 Načte ukazatele rozhraní k spojovací bod, který podporuje zadaná IID.  
  
```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [Přehled třídy](../../atl/atl-class-overview.md)
