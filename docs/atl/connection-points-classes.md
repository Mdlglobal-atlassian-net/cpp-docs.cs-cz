---
title: "Třídy body připojení (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.connection
dev_langs: C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e85194547b78e3d3fa3bba868be02c705fcf9a43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

