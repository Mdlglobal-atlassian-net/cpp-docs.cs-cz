---
title: IConnectionPointImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: bd88fd5d00df0347c0bd2161129b8cfa3ca35406
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496085"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl – třída

Tato třída implementuje bod připojení.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IConnectionPointImpl`odvozena z.

*piid*<br/>
Ukazatel na IID rozhraní reprezentovaného objektem spojovacího bodu.

*CDV*<br/>
Třída, která spravuje připojení. Výchozí hodnota je [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), která umožňuje neomezená připojení. Můžete také použít [CComUnkArray](../../atl/reference/ccomunkarray-class.md), který určuje pevný počet připojení.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IConnectionPointImpl::Advise](#advise)|Naváže spojení mezi spojovacím bodem a jímkou.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Vytvoří enumerátor pro iteraci přes připojení pro bod připojení.|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Načte IID rozhraní reprezentované bodem připojení.|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Načte ukazatel rozhraní na připojovatelné objekty.|
|[IConnectionPointImpl::Unadvise](#unadvise)|Ukončí připojení, které bylo dříve vytvořeno `Advise`prostřednictvím.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|Spravuje připojení k bodu připojení.|

## <a name="remarks"></a>Poznámky

`IConnectionPointImpl`implementuje bod připojení, který objektu umožňuje vystavit odchozí rozhraní klientovi. Klient implementuje toto rozhraní u objektu s názvem jímka.

ATL používá [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) k implementaci připojeného objektu. Každý bod připojení v rámci připojeného objektu představuje výstupní rozhraní identifikované *piid*. Třída *CDV* spravuje připojení mezi spojovacím bodem a jímkou. Každé připojení je jednoznačně identifikované souborem cookie.

Další informace o použití bodů připojení v knihovně ATL najdete v článku [body připojení](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="advise"></a>  IConnectionPointImpl::Advise

Naváže spojení mezi spojovacím bodem a jímkou.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Poznámky

K [](#unadvise) ukončení volání připojení použijte Unadvise.

Viz [IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) v Windows SDK.

##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections

Vytvoří enumerátor pro iteraci přes připojení pro bod připojení.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPoint:: EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) v Windows SDK.

##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface

Načte IID rozhraní reprezentované bodem připojení.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPoint:: GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) v Windows SDK.

##  <a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer

Načte ukazatel rozhraní na připojovatelné objekty.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPoint:: GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) v Windows SDK.

##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec

Spravuje připojení mezi objektem spojovacího bodu a jímkou.

```
CDV m_vec;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `m_vec` je typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

##  <a name="unadvise"></a>IConnectionPointImpl:: Unadvise

Ukončí připojení, které bylo dříve vytvořeno prostřednictvím [Advise](#advise).

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPoint:: Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) v Windows SDK.

## <a name="see-also"></a>Viz také:

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
