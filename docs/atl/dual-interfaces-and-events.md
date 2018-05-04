---
title: Duální rozhraní a události | Microsoft Docs
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
ms.openlocfilehash: 99dc173f3dde8ea81f6dc11d02298cd94673f999
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="dual-interfaces-and-events"></a>Duální rozhraní a události
I když je možné k návrhu událostí rozhraní jako duální, existuje několik důvodů dobrý návrh není to udělat. Základní důvodem je skutečnost, že zdroj události bude platit pouze událostí prostřednictvím tabulce vtable nebo prostřednictvím `Invoke`, ne pomocí obou. Pokud zdroj události aktivuje událost jako přímý vtable volání metody, `IDispatch` metody nebude nikdy používat a je zřejmé, že rozhraní by byla čistý vtable rozhraní. Pokud zdroj události aktivuje událost jako volání `Invoke`, metody vtable nebude nikdy používat a je jasné, že rozhraní by byla odesílajícím rozhraním. Pokud definujete vašich rozhraní událostí jako duals, budete vyžadující klientům implementovat součástí rozhraní, které se nikdy používat.  
  
> [!NOTE]
>  Tento argument se nevztahuje duální rozhraní obecně. Z hlediska implementaci duals jsou rychlé, pohodlný a dobře podporované způsob implementace rozhraní, které jsou dostupné k široké škále klientů.  
  
 Existují další důvodů, aby se zabránilo duální událostí rozhraní; Visual Basic ani aplikace Internet Explorer je podporují.  
  
## <a name="see-also"></a>Viz také  
 [Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

