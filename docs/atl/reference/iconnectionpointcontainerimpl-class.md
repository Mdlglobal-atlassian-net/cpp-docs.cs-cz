---
title: IConnectionPointContainerImpl – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 5931d12acfead0a3832e84c3008bfde2ffd4a8d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077670"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl – třída

Tato třída implementuje kontejner bod připojení pro správu kolekce [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objekty.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IConnectionPointContainerImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Vytvoří čítač k iteraci v rámci spojovací body v umožňující připojení k objektu podporována.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Načte ukazatel do bodu připojení, která podporuje zadaný identifikátor IID rozhraní.|

## <a name="remarks"></a>Poznámky

`IConnectionPointContainerImpl` implementuje kontejner bod připojení pro správu kolekce [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objekty. `IConnectionPointContainerImpl` nabízí dvě metody, které klient volat, když Chci získat další informace o umožňující připojení k objektu:

- `EnumConnectionPoints` umožňuje klientovi k určení, které odchozí rozhraní podporuje objektu.

- `FindConnectionPoint` umožňuje klientovi k určení, zda objekt podporuje určité odchozí rozhraní.

Informace o použití spojovacích bodů v ATL, najdete v článku [spojovací body](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints

Vytvoří čítač k iteraci v rámci spojovací body v umožňující připojení k objektu podporována.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IConnectionPointContainer::EnumConnectionPoints](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) ve Windows SDK.

##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint

Načte ukazatel do bodu připojení, která podporuje zadaný identifikátor IID rozhraní.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IConnectionPointContainer::FindConnectionPoint](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) ve Windows SDK.

## <a name="see-also"></a>Viz také

[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
