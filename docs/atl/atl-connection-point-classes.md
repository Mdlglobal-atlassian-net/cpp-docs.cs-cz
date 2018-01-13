---
title: "Třídy ATL připojení bodu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9845fdffdd951809ee7127c5fec86097a6219354
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-connection-point-classes"></a>ATL – třídy bodu připojení
ATL používá následující třídy pro podporu spojovací body:  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje bod připojení. Identifikátory IID rozhraní odchozí, který představuje se předá jako parametr šablony.  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) kontejner bodu připojení implementuje a spravuje seznam `IConnectionPointImpl` objekty.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje představující bod připojení [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní.  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) spravuje libovolný počet připojení mezi bodem připojení a jeho jímky.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) spravuje předdefinované počet připojení podle specifikace parametr šablony.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) upozorní podřízený klienta, který vlastnost objektu došlo ke změně nebo se chystáte se změnit.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) poskytuje podporu pro spojovací body pro objekt ATL COM. Tyto body připojení jsou namapována na jímka mapa událostí, které zajišťuje objektu COM.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) funguje ve spojení s mapy jímek událostí ve třídě události trasy k funkci příslušnou obslužnou rutinu.  
  
## <a name="see-also"></a>Viz také  
 [Spojovací bod](../atl/atl-connection-points.md)

