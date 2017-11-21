---
title: "Třída IPropertyNotifySinkCP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs: C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 91e2bcff0b168e9238351cff623f888221b583b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 `IPropertyNotifySinkCP`dědí všechny metody prostřednictvím její základní třída [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní, které umožňuje podřízený objekt k přijímání oznámení o změnách vlastnost. Třída `IPropertyNotifySinkCP` zpřístupní toto rozhraní jako odchozí rozhraní na objekt umožňující připojení. Klient musí implementovat `IPropertyNotifySink` metody na jímky.  
  
 Odvození třídě z `IPropertyNotifySinkCP` když chcete vytvořit spojovací bod, který představuje `IPropertyNotifySink` rozhraní.  
  
 Další informace o používání v ATL – body připojení, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
## <a name="see-also"></a>Viz také  
 [IConnectionPointImpl – třída](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl – třída](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
