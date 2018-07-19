---
title: Ipropertynotifysinkcp – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 66fd7b267a70b962bb5c28bb5835bd96d44a92f0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879186"
---
# <a name="ipropertynotifysinkcp-class"></a>Ipropertynotifysinkcp – třída
Tato třída zveřejňuje [ipropertynotifysink –](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní jako odchozí rozhraní umožňující připojení k objektu.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IPropertyNotifySinkCP`.  
  
 *CDV*  
 Třída, která spravuje připojení mezi bodem připojení a jeho jímky. Výchozí hodnota je [ccomdynamicunkarray –](../../atl/reference/ccomdynamicunkarray-class.md), který umožňuje neomezený počet připojení. Můžete také použít [ccomunkarray –](../../atl/reference/ccomunkarray-class.md), která určuje pevný počet připojení.  
  
## <a name="remarks"></a>Poznámky  
 `IPropertyNotifySinkCP` dědí všechny metody prostřednictvím její základní třídě [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 [Ipropertynotifysink –](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní umožňuje vnořený objekt k přijímání oznámení o změně vlastnosti. Třída `IPropertyNotifySinkCP` zpřístupní toto rozhraní jako odchozí rozhraní umožňující připojení k objektu. Klient musí implementovat `IPropertyNotifySink` metody na jímce.  
  
 Odvodit třídu z `IPropertyNotifySinkCP` Pokud chcete vytvořit, který představuje bod připojení `IPropertyNotifySink` rozhraní.  
  
 Další informace o použití spojovacích bodů v ATL, najdete v článku [spojovací body](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
## <a name="see-also"></a>Viz také  
 [IConnectionPointImpl – třída](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl – třída](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
