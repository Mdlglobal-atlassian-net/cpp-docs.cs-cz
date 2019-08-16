---
title: IConnectionPointContainerImpl Class
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
ms.openlocfilehash: 278ca6b1b9aac9539680d90b6fa0b18df22fc2f0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496015"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl Class

Tato třída implementuje kontejner spojovacího bodu pro správu kolekce objektů [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IConnectionPointContainerImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Vytvoří enumerátor pro iteraci přes spojovací body podporované objektem, který lze připojit.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Načte ukazatel rozhraní na spojovací bod, který podporuje zadaný identifikátor IID.|

## <a name="remarks"></a>Poznámky

`IConnectionPointContainerImpl`implementuje kontejner spojovacího bodu pro správu kolekce objektů [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) . `IConnectionPointContainerImpl`poskytuje dvě metody, které může klient volat a získat další informace o připojeném objektu:

- `EnumConnectionPoints`umožňuje klientovi určit, která odchozí rozhraní objekt podporuje.

- `FindConnectionPoint`umožňuje klientovi určit, zda objekt podporuje konkrétní odchozí rozhraní.

Informace o použití bodů připojení v knihovně ATL najdete v článku [body připojení](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints

Vytvoří enumerátor pro iteraci přes spojovací body podporované objektem, který lze připojit.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPointContainer:: EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) v Windows SDK.

##  <a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint

Načte ukazatel rozhraní na spojovací bod, který podporuje zadaný identifikátor IID.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) v Windows SDK.

## <a name="see-also"></a>Viz také:

[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
