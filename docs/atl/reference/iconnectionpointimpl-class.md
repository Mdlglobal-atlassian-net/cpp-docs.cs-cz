---
title: "Třída IConnectionPointImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
dev_langs: C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c3e51322b5ac94688e39c0b4ebad1649a5a25d4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl – třída
Tato třída implementuje bod připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IConnectionPointImpl`.  
  
 `piid`  
 Ukazatel na identifikátory IID rozhraní reprezentována objektu bodu připojení.  
  
 `CDV`  
 Třída, která spravuje připojení. Výchozí hodnota je [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), což umožňuje neomezený počet připojení. Můžete také použít [CComUnkArray](../../atl/reference/ccomunkarray-class.md), která určuje pevný počet připojení.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|Naváže připojení mezi bodem připojení a jímky.|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Vytvoří enumerátor k iteraci v rámci připojení pro spojovacího bodu.|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Načte identifikátory IID rozhraní reprezentována spojovacího bodu.|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Načte ukazatele rozhraní k objektu umožňující připojení.|  
|[IConnectionPointImpl::Unadvise](#unadvise)|Ukončí připojení dříve vytvořené prostřednictvím `Advise`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|Spravuje připojení pro spojovacího bodu.|  
  
## <a name="remarks"></a>Poznámky  
 `IConnectionPointImpl`implementuje bod připojení, která umožňuje objekt vystavit odchozí rozhraní klientovi. Klient pro toto rozhraní implementuje na názvem podřízený objekt.  
  
 ATL používá [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) implementovat objekt umožňující připojení. Každý bod připojení v rámci umožňující připojení objektu představuje odchozí rozhraní, identifikovaný `piid`. Třída *CDV* spravuje připojení mezi bodem připojení a jímky. Každé připojení je jedinečně identifikovaný "souboru cookie."  
  
 Další informace o používání v ATL – body připojení, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="advise"></a>IConnectionPointImpl::Advise  
 Naváže připojení mezi bodem připojení a jímky.  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>Poznámky  
 Použití [Unadvise](#unadvise) ukončit připojení volání.  
  
 V tématu [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) ve Windows SDK.  
  
##  <a name="enumconnections"></a>IConnectionPointImpl::EnumConnections  
 Vytvoří enumerátor k iteraci v rámci připojení pro spojovacího bodu.  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IConnectionPoint::EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755) ve Windows SDK.  
  
##  <a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface  
 Načte identifikátory IID rozhraní reprezentována spojovacího bodu.  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IConnectionPoint::GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468) ve Windows SDK.  
  
##  <a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer  
 Načte ukazatele rozhraní k objektu umožňující připojení.  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IConnectionPoint::GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669) ve Windows SDK.  
  
##  <a name="m_vec"></a>IConnectionPointImpl::m_vec  
 Spravuje připojení mezi objektu bodu připojení a jímky.  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `m_vec` je typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).  
  
##  <a name="unadvise"></a>IConnectionPointImpl::Unadvise  
 Ukončí připojení dříve vytvořené prostřednictvím [doporučení](#advise).  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IConnectionPoint –](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Přehled třídy](../../atl/atl-class-overview.md)
