---
title: Třída IConnectionPointContainerImpl
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
ms.openlocfilehash: f6009a1341d6715d6d2f170d3ff2aa1aa4ffcb96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329869"
---
# <a name="iconnectionpointcontainerimpl-class"></a>Třída IConnectionPointContainerImpl

Tato třída implementuje kontejner spojovacího bodu pro správu kolekce objektů [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md)

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IConnectionPointContainerImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Vytvoří čítač enumeratátorit prostřednictvím spojovacích bodů podporovaných v připojitelný objekt.|
|[iConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Načte ukazatel rozhraní do bodu připojení, který podporuje zadané IID.|

## <a name="remarks"></a>Poznámky

`IConnectionPointContainerImpl`implementuje kontejner spojovacího bodu pro správu kolekce objektů [IConnectionPointImpl.](../../atl/reference/iconnectionpointimpl-class.md) `IConnectionPointContainerImpl`Poskytuje dvě metody, které může klient volat k načtení dalších informací o připojitelném objektu:

- `EnumConnectionPoints`umožňuje klientovi určit, která odchozí rozhraní objekt podporuje.

- `FindConnectionPoint`umožňuje klientovi určit, zda objekt podporuje určité odchozí rozhraní.

Informace o použití spojovacích bodů v atl naleznete v článku [Spojovací body](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="iconnectionpointcontainerimplenumconnectionpoints"></a><a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints

Vytvoří čítač enumeratátorit prostřednictvím spojovacích bodů podporovaných v připojitelný objekt.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPointContainer::EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) v sadě Windows SDK.

## <a name="iconnectionpointcontainerimplfindconnectionpoint"></a><a name="findconnectionpoint"></a>iConnectionPointContainerImpl::FindConnectionPoint

Načte ukazatel rozhraní do bodu připojení, který podporuje zadané IID.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Iconnectionpointcontainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
