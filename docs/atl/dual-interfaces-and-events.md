---
title: Duální rozhraní a události
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 4ce5048c25bd55feb0f1eb20fc04ec6bfeead746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319609"
---
# <a name="dual-interfaces-and-events"></a>Duální rozhraní a události

I když je možné navrhnout rozhraní události jako duální, existuje řada dobrých důvodů návrhu, aby tak neučinily. Základním důvodem je, že zdroj události bude pouze oheň `Invoke`událost přes vtable nebo přes , ne obojí. Pokud zdroj události spustí událost jako volání metody `IDispatch` přímé vtable, metody se nikdy nepoužijí a je jasné, že rozhraní by mělo být čistě vtable rozhraní. Pokud zdroj události spustí událost jako `Invoke`volání , vtable metody se nikdy nepoužije a je jasné, že rozhraní by měly být dispinterface. Pokud definujete rozhraní událostí jako duals, budete vyžadovat, aby klienti implementovali část rozhraní, která se nikdy nebude používat.

> [!NOTE]
> Tento argument se obecně nevztahuje na duální rozhraní. Z hlediska implementace jsou diody rychlým, pohodlným a dobře podporovaným způsobem implementace rozhraní, která jsou přístupná širokému spektru klientů.

Existují další důvody, aby se zabránilo duální události rozhraní; Jazyk Visual Basic ani aplikace Internet Explorer je nepodporují.

## <a name="see-also"></a>Viz také

[Duální rozhraní a knihovna ATL](../atl/dual-interfaces-and-atl.md)
