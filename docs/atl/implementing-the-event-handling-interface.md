---
title: Implementace rozhraní zpracování událostí | Dokumentace Microsoftu
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
ms.openlocfilehash: b2241080fda6aa58dc5e70f57c83afec69a57203
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757335"
---
# <a name="implementing-the-event-handling-interface"></a>Implementace rozhraní zpracování událostí

ATL – pomáhá všech tří prvků vyžadovaných pro zpracování událostí: implementace událostí rozhraní předobjednávky zdroj události a unadvising zdroje událostí. Přesné kroky, které je potřeba provést závisí na typ rozhraní události a požadavky na výkon vaší aplikace.

Nejběžnější způsoby implementace rozhraní pomocí knihovny ATL jsou:

- Odvozování z vlastního rozhraní přímo.

- Odvozování z [třídou IDispatchImpl](../atl/reference/idispatchimpl-class.md) pro duální rozhraní, které jsou popsané v knihovně typů.

- Odvozování z [IDispEventImpl](../atl/reference/idispeventimpl-class.md) pro odesílající rozhraní je popsáno v knihovně typů.

- Odvozování z [idispeventsimpleimpl –](../atl/reference/idispeventsimpleimpl-class.md) pro odesílacích rozhraních není popsána v knihovně typů nebo pokud chcete zvýšit efektivitu není načítání informací o typu v době běhu.

Pokud implementujete vlastní nebo duální rozhraní, poraďte zdroj události voláním [AtlAdvise](reference/connection-point-global-functions.md#atladvise) nebo [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise). Je potřeba udržovat přehled o souboru cookie vrácený voláním sami. Volání [AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise) přerušit připojení.  

Pokud implementujete dispinterface pomocí `IDispEventImpl` nebo `IDispEventSimpleImpl`, zdroj události poraďte voláním [IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise). Volání [IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise) přerušit připojení.

Pokud používáte `IDispEventImpl` jako základní třída složeného ovládacího prvku zdroje událostí uvedený v mapování jímky bude doporučené a unadvised automaticky pomocí [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).

`IDispEventImpl` a `IDispEventSimpleImpl` třídy soubor cookie spravovat za vás.

## <a name="see-also"></a>Viz také

[Zpracování událostí](../atl/event-handling-and-atl.md)

