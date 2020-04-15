---
title: Třída IConnectionpointimpl
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
ms.openlocfilehash: c62ac3310a579379674674a7a9a517e3f2fd60e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329858"
---
# <a name="iconnectionpointimpl-class"></a>Třída IConnectionpointimpl

Tato třída implementuje spojovací bod.

## <a name="syntax"></a>Syntaxe

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IConnectionPointImpl`.

*piid*<br/>
Ukazatel na IID rozhraní reprezentovaného objektem spojovacího bodu.

*Cdv*<br/>
Třída, která spravuje připojení. Výchozí hodnota je [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), která umožňuje neomezené připojení. Můžete také použít [CComUnkArray](../../atl/reference/ccomunkarray-class.md), který určuje pevný počet připojení.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IConnectionpointimpl::Poradit](#advise)|Naváže spojení mezi bodem připojení a jímkou.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Vytvoří čítač enumeratator iterate prostřednictvím připojení pro bod připojení.|
|[iConnectionPointimpl::GetConnectionInterface](#getconnectioninterface)|Načte IID rozhraní reprezentovaného spojovacím bodem.|
|[iConnectionPointimpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Načte ukazatel rozhraní k připojitelnému objektu.|
|[IConnectionPointImpl::Nerada](#unadvise)|Ukončí připojení dříve navázána prostřednictvím `Advise`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|Spravuje připojení pro spojovací bod.|

## <a name="remarks"></a>Poznámky

`IConnectionPointImpl`implementuje spojovací bod, který umožňuje objektu vystavit odchozí rozhraní klientovi. Klient implementuje toto rozhraní na objekt s názvem jímky.

Knihovna ATL používá k implementaci připojitelného objektu [iConnectionPointContainerImpl.](../../atl/reference/iconnectionpointcontainerimpl-class.md) Každý spojovací bod v objektu připojitelném představuje odchozí rozhraní označené *piid*. Třída *CDV* spravuje připojení mezi bodem připojení a jímkou. Každé připojení je jednoznačně označeno souborem cookie.

Další informace o použití spojovacích bodů v atl naleznete v článku [Spojovací body](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a>IConnectionpointimpl::Poradit

Naváže spojení mezi bodem připojení a jímkou.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Poznámky

K ukončení volání připojení použijte [unadvise.](#unadvise)

Viz [IConnectionPoint::Advise v](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) sadě Windows SDK.

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a>IConnectionPointImpl::EnumConnections

Vytvoří čítač enumeratator iterate prostřednictvím připojení pro bod připojení.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPoint::EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) v sadě Windows SDK.

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a>iConnectionPointimpl::GetConnectionInterface

Načte IID rozhraní reprezentovaného spojovacím bodem.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPoint::GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) v sadě Windows SDK.

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a>iConnectionPointimpl::GetConnectionPointContainer

Načte ukazatel rozhraní k připojitelnému objektu.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPoint::GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) v sadě Windows SDK.

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a>IConnectionPointImpl::m_vec

Spravuje připojení mezi objektem spojovacího bodu a jímkou.

```
CDV m_vec;
```

### <a name="remarks"></a>Poznámky

Ve výchozím `m_vec` nastavení je typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a>IConnectionPointImpl::Nerada

Ukončí připojení dříve navázána prostřednictvím [Advise](#advise).

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Poznámky

Viz [IConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
