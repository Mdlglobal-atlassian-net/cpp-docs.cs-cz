---
title: "Správa paměti: Bloky paměti umožňující změnu velikosti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fce06d27a091ad1740c882367358cf69a6dc3e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-resizable-memory-blocks"></a>Správa paměti: Paměťové bloky umožňující změnu velikosti
**Nové** a **odstranit** operátory, které jsou popsané v článku [Správa paměti: Příklady](../mfc/memory-management-examples.md), jsou vhodné pro přidělování a rušení přidělení bloků paměti pevné velikosti a objekty. Aplikace v některých případech může být nutné bloky paměti umožňující změnu velikosti. Musí používat standardní funkce běhové knihovny jazyka C [malloc –](../c-runtime-library/reference/malloc.md), [realloc –](../c-runtime-library/reference/realloc.md), a [volné](../c-runtime-library/reference/free.md) ke správě bloky paměti umožňující změnu velikosti v haldě.  
  
> [!IMPORTANT]
>  Kombinování **nové** a **odstranit** operátory s funkcí s možností změny velikosti přidělení paměti na stejný blok paměti bude mít za následek poškozená paměti v ladicí verze knihovny MFC. Neměli byste používat `realloc` na blok paměti přidělené s **nové**. Stejně tak by neměl přidělit paměť blok s **nové** operátor a odstranit ji s **volné**, nebo použijte **odstranit** operátor na blok paměti přidělené s `malloc`.  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti: Přidělení haldy](../mfc/memory-management-heap-allocation.md)

