---
title: Duální rozhraní a události | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a482486be66811954602849c4bdde5b8955c887f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763211"
---
# <a name="dual-interfaces-and-events"></a>Duální rozhraní a události

I když je možné navrhnout jako duální rozhraní události, existuje mnoho důvodů dobrý návrh není k tomu. Základní důvodem je, že zdroj události se pouze aktivuje události prostřednictvím tabulku vtable nebo prostřednictvím `Invoke`, ne obě možnosti současně. Pokud zdroj události vyvolá událost jako volání metody s přímým přístupem vtable, `IDispatch` metody se nikdy nepoužívá a je jasné, že rozhraní by musela být čistě vtable rozhraní. Pokud zdroj události vyvolá událost jako volání `Invoke`metody tabulku vtable se nikdy nepoužívá a je jasné, že rozhraní by byly dispinterface. Pokud definujete událostních rozhraní jako duals, budete vyžadující klienty k implementaci součástí rozhraní, které se nikdy nepoužívá.

> [!NOTE]
>  Tento argument se nevztahují na duální rozhraní, Obecné. Z hlediska implementace jsou duals snadné, pohodlné a dobře podporovaným způsobem implementace rozhraní, které jsou přístupné pro širokou škálu klientů.

Existují další důvody k vyhnout duální rozhraní; Visual Basic ani aplikace Internet Explorer je podporují.

## <a name="see-also"></a>Viz také

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

