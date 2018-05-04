---
title: Implementace rozhraní zpracování událostí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, event handling
- event handling, ATL
- interfaces, event and event sink
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea37aa4c84cb0824d11f0081e38d9e8157b77ed1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-the-event-handling-interface"></a>Implementace rozhraní zpracování událostí
ATL vám pomůže s všechny tři prvky, které jsou požadované pro zpracování událostí: implementace událostí rozhraní radí zdroj události a unadvising zdroj události. Přesné kroky, které budete muset provést závisí na typu rozhraní událostí a požadavky na výkon vaší aplikace.  
  
 Nejběžnější způsoby implementace rozhraní pomocí knihovny ATL jsou:  
  
-   Odvozování z vlastní rozhraní přímo.  
  
-   Odvozování z [IDispatchImpl](../atl/reference/idispatchimpl-class.md) pro duální rozhraní, které jsou popsané v knihovny typů.  
  
-   Odvozování z [IDispEventImpl](../atl/reference/idispeventimpl-class.md) pro odesílající rozhraní popsané v knihovny typů.  
  
-   Odvozování z [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) pro odesílající rozhraní není popsána v knihovny typů, nebo pokud chcete zlepšit efektivitu není načítání informací o typu při běhu.  
  

 Pokud implementujete vlastní nebo duální rozhraní, poraďte zdroj události voláním [AtlAdvise](reference/connection-point-global-functions.md#atladvise) nebo [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise). Musíte se ke sledování souboru cookie vrácený volání. Volání [AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise) k přerušení připojení.  

  
 Pokud implementujete dispinterface pomocí `IDispEventImpl` nebo `IDispEventSimpleImpl`, poraďte zdroj události voláním [IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise). Volání [IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise) k přerušení připojení.  
  
 Pokud používáte `IDispEventImpl` jako základní třída složeného ovládacího prvku, bude zdroje událostí, které jsou uvedeny v mapě podřízený doporučené a unadvised automaticky pomocí [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).  
  
 `IDispEventImpl` a `IDispEventSimpleImpl` třídy spravovat souboru cookie, který pro vás.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování událostí](../atl/event-handling-and-atl.md)

