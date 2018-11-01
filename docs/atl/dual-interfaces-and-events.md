---
title: Duální rozhraní a události
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: f94e87f077846af8d61b06145f776f385051e79f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640593"
---
# <a name="dual-interfaces-and-events"></a>Duální rozhraní a události

I když je možné navrhnout jako duální rozhraní události, existuje mnoho důvodů dobrý návrh není k tomu. Základní důvodem je, že zdroj události se pouze aktivuje události prostřednictvím tabulku vtable nebo prostřednictvím `Invoke`, ne obě možnosti současně. Pokud zdroj události vyvolá událost jako volání metody s přímým přístupem vtable, `IDispatch` metody se nikdy nepoužívá a je jasné, že rozhraní by musela být čistě vtable rozhraní. Pokud zdroj události vyvolá událost jako volání `Invoke`metody tabulku vtable se nikdy nepoužívá a je jasné, že rozhraní by byly dispinterface. Pokud definujete událostních rozhraní jako duals, budete vyžadující klienty k implementaci součástí rozhraní, které se nikdy nepoužívá.

> [!NOTE]
>  Tento argument se nevztahují na duální rozhraní, Obecné. Z hlediska implementace jsou duals snadné, pohodlné a dobře podporovaným způsobem implementace rozhraní, které jsou přístupné pro širokou škálu klientů.

Existují další důvody k vyhnout duální rozhraní; Visual Basic ani aplikace Internet Explorer je podporují.

## <a name="see-also"></a>Viz také

[Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

