---
title: Třída IPropertyNotifySinkCP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9612cf65479e474b9a6e89a8f5a57ca078c9ed0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP – třída
Tato třída zpřístupňuje [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní jako odchozí rozhraní na objekt umožňující připojení.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IPropertyNotifySinkCP`.  
  
 `CDV`  
 Třída, která spravuje připojení mezi bod připojení a jeho jímky. Výchozí hodnota je [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), což umožňuje neomezený počet připojení. Můžete také použít [CComUnkArray](../../atl/reference/ccomunkarray-class.md), která určuje pevný počet připojení.  
  
## <a name="remarks"></a>Poznámky  
 `IPropertyNotifySinkCP` dědí všechny metody prostřednictvím její základní třída [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní, které umožňuje podřízený objekt k přijímání oznámení o změnách vlastnost. Třída `IPropertyNotifySinkCP` zpřístupní toto rozhraní jako odchozí rozhraní na objekt umožňující připojení. Klient musí implementovat `IPropertyNotifySink` metody na jímky.  
  
 Odvození třídě z `IPropertyNotifySinkCP` když chcete vytvořit spojovací bod, který představuje `IPropertyNotifySink` rozhraní.  
  
 Další informace o používání v ATL – body připojení, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
## <a name="see-also"></a>Viz také  
 [IConnectionPointImpl – třída](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl – třída](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
