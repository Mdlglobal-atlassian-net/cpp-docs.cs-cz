---
title: "Správa paměti | Microsoft Docs"
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
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a9e31fc1136249f843aa5dc96a4caffcccc7a85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management"></a>Správa paměti
Tato skupina článků popisuje, jak využít pro obecné účely služby z Microsoft Foundation Class knihovny (MFC) související se správou paměti. Přidělení paměti je možné rozdělit do dvou hlavních kategorií: rámce přidělení a přidělení haldy.  
  
 Jeden hlavní rozdíl mezi dvěma přidělení techniky je, že s přidělení rámce, který obvykle pracujete s skutečné paměti blokovat samostatně, když s přidělení haldy jsou vždy uvedeny ukazatel k bloku paměti. Další hlavní rozdíl mezi dvěma schémata je, že rámce objekty jsou automaticky odstraněny, při haldy objekty se musí explicitně odstranit programátorem.  
  
 Mimo MFC informace o správě paměti v aplikacích pro Windows najdete v tématu [Správa paměti](http://msdn.microsoft.com/library/windows/desktop/aa366779) ve Windows SDK.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Přidělení rámce](../mfc/memory-management-frame-allocation.md)  
  
-   [Přidělení haldy](../mfc/memory-management-heap-allocation.md)  
  
-   [Přidělení paměti pro pole](../mfc/memory-management-examples.md)  
  
-   [Zrušení přidělení paměti pro pole z haldy](../mfc/memory-management-examples.md)  
  
-   [Přidělení paměti pro datová struktura](../mfc/memory-management-examples.md)  
  
-   [Přidělení paměti pro objekt](../mfc/memory-management-examples.md)  
  
-   [Bloky paměti umožňující změnu velikosti](../mfc/memory-management-resizable-memory-blocks.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)   
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

