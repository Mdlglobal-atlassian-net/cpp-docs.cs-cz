---
title: "Třídy body připojení (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.atl.connection
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa0ef8139c659b5085b20709e0c96ab2bf821ce4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="connection-points-classes"></a>Třídy body připojení
Následující třídy poskytují podporu pro spojovací body:  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementuje kontejner bod připojení.  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementuje bod připojení.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementuje představující bod připojení [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) rozhraní.  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) spravuje neomezený počet připojení mezi bod připojení a jeho jímky.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) spravuje pevný počet připojení mezi bod připojení a jeho jímky.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) upozorní podřízený klienta, který vlastnost objektu došlo ke změně nebo se chystáte se změnit.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) poskytuje podporu pro spojovací body pro objekt ATL COM. Tyto body připojení jsou namapována na jímka mapa událostí, které zajišťuje objektu COM.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) funguje ve spojení s jímky událostí mapy ve třídě události trasy k funkci příslušnou obslužnou rutinu.  
  
## <a name="related-articles"></a>Související články  
 [Body připojení](../atl/atl-connection-points.md)  
  
 [Zpracování událostí a ATL](../atl/event-handling-and-atl.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../atl/atl-class-overview.md)   
 [Makra bodu připojení](../atl/reference/connection-point-macros.md)   
 [Globální funkce bodů připojení](../atl/reference/connection-point-global-functions.md)

