---
title: Správa paměti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28191191572e508828a23f0e719a57d63163b08d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222348"
---
# <a name="memory-management"></a>Správa paměti
Tato skupina článků popisuje, jak využít univerzální služby z třídy knihovny MFC (Microsoft Foundation) týkající se správy paměti. Přidělení paměti je možné rozdělit do dvou hlavních kategorií: rámec přidělení a přidělení haldy.  
  
 Jedním z hlavních rozdílů mezi dvěma přidělení techniky je, že s přidělení rámce, které většinou pracují s skutečná paměť blokovat, zatímco s přidělení haldy jsou vždy uvedeny ukazatele na blok paměti. Další hlavní rozdíl mezi dvě schémata je, že rámec objekty jsou automaticky odstraní, zatímco objektů haldy se musí explicitně odstranit programátorem.  
  
 MFC – informace o správě paměti v aplikacích pro Windows najdete v tématu [Správa paměti](https://msdn.microsoft.com/library/windows/desktop/aa366779) v sadě Windows SDK.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací  
  
-   [Přidělení rámce](../mfc/memory-management-frame-allocation.md)  
  
-   [Přidělení haldy](../mfc/memory-management-heap-allocation.md)  
  
-   [Přidělení paměti pro pole](../mfc/memory-management-examples.md)  
  
-   [Rušení přidělení paměti pro pole z haldy](../mfc/memory-management-examples.md)  
  
-   [Přidělení paměti pro datové struktury](../mfc/memory-management-examples.md)  
  
-   [Přidělení paměti pro objekt](../mfc/memory-management-examples.md)  
  
-   [Bloky paměti umožňující změnu velikosti](../mfc/memory-management-resizable-memory-blocks.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)   
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

