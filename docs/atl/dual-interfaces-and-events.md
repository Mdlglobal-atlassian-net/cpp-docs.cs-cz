---
title: "Duální rozhraní a události | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 87774f0237eb42c4bd2f97185230b3c869688ca8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dual-interfaces-and-events"></a>Duální rozhraní a události
I když je možné k návrhu událostí rozhraní jako duální, existuje několik důvodů dobrý návrh není to udělat. Základní důvodem je skutečnost, že zdroj události bude platit pouze událostí prostřednictvím tabulce vtable nebo prostřednictvím `Invoke`, ne pomocí obou. Pokud zdroj události aktivuje událost jako přímý vtable volání metody, `IDispatch` metody nebude nikdy používat a je zřejmé, že rozhraní by byla čistý vtable rozhraní. Pokud zdroj události aktivuje událost jako volání `Invoke`, metody vtable nebude nikdy používat a je jasné, že rozhraní by byla odesílajícím rozhraním. Pokud definujete vašich rozhraní událostí jako duals, budete vyžadující klientům implementovat součástí rozhraní, které se nikdy používat.  
  
> [!NOTE]
>  Tento argument se nevztahuje duální rozhraní obecně. Z hlediska implementaci duals jsou rychlé, pohodlný a dobře podporované způsob implementace rozhraní, které jsou dostupné k široké škále klientů.  
  
 Existují další důvodů, aby se zabránilo duální událostí rozhraní; Visual Basic ani aplikace Internet Explorer je podporují.  
  
## <a name="see-also"></a>Viz také  
 [Duální rozhraní a ATL](../atl/dual-interfaces-and-atl.md)

