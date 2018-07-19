---
title: IConnectionPointImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf1f012067c3a3b85dd5168cf93521e4b2024e00
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884038"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl – třída
Tato třída implementuje bod připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IConnectionPointImpl`.  
  
 *piid*  
 Ukazatel na IID rozhraní reprezentovaný objektem bodu připojení.  
  
 *CDV*  
 Třída, která spravuje připojení. Výchozí hodnota je [ccomdynamicunkarray –](../../atl/reference/ccomdynamicunkarray-class.md), který umožňuje neomezený počet připojení. Můžete také použít [ccomunkarray –](../../atl/reference/ccomunkarray-class.md), která určuje pevný počet připojení.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|Naváže připojení mezi bodem připojení a jímku.|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Vytvoří čítač k iteraci v rámci připojení bodu připojení.|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Načte identifikátor IID rozhraní reprezentována spojovací bod.|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Načte ukazatel rozhraní umožňující připojení k objektu.|  
|[IConnectionPointImpl::Unadvise](#unadvise)|Ukončí připojení dříve vytvořené prostřednictvím `Advise`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|Spravuje připojení bodu připojení.|  
  
## <a name="remarks"></a>Poznámky  
 `IConnectionPointImpl` implementuje bod připojení, což umožňuje vystavit odchozí rozhraní do klienta. Klient implementuje toto rozhraní na objektu s názvem jímky.  
  
 ATL – používá [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) implementovat umožňující připojení k objektu. Každý bod připojení v rámci umožňující připojení k objektu představuje odchozí rozhraní, identifikovaný *piid*. Třída *CDV* spravuje připojení mezi bodem připojení a jímku. Každé připojení je jedinečně identifikovaný "souboru cookie."  
  
 Další informace o použití spojovacích bodů v ATL, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="advise"></a>  IConnectionPointImpl::Advise  
 Naváže připojení mezi bodem připojení a jímku.  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>Poznámky  
 Použití [Unadvise](#unadvise) ukončení volání připojení.  
  
 Zobrazit [IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) ve Windows SDK.  
  
##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections  
 Vytvoří čítač k iteraci v rámci připojení bodu připojení.  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IConnectionPoint::EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755) ve Windows SDK.  
  
##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface  
 Načte identifikátor IID rozhraní reprezentována spojovací bod.  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IConnectionPoint::GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468) ve Windows SDK.  
  
##  <a name="getconnectionpointcontainer"></a>  IConnectionPointImpl::GetConnectionPointContainer  
 Načte ukazatel rozhraní umožňující připojení k objektu.  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IConnectionPoint::GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669) ve Windows SDK.  
  
##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec  
 Spravuje připojení mezi objektu bodu připojení a jímku.  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `m_vec` je typu [ccomdynamicunkarray –](../../atl/reference/ccomdynamicunkarray-class.md).  
  
##  <a name="unadvise"></a>  IConnectionPointImpl::Unadvise  
 Ukončí připojení dříve vytvořené prostřednictvím [doporučení](#advise).  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Přehled tříd](../../atl/atl-class-overview.md)
