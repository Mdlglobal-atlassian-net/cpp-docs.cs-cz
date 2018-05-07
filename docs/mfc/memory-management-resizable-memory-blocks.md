---
title: 'Správa paměti: Bloky paměti umožňující změnu velikosti | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bbd97899261f85454824fcab261d330b04e25fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="memory-management-resizable-memory-blocks"></a>Správa paměti: Paměťové bloky umožňující změnu velikosti
**Nové** a **odstranit** operátory, které jsou popsané v článku [Správa paměti: Příklady](../mfc/memory-management-examples.md), jsou vhodné pro přidělování a rušení přidělení bloků paměti pevné velikosti a objekty. Aplikace v některých případech může být nutné bloky paměti umožňující změnu velikosti. Musí používat standardní funkce běhové knihovny jazyka C [malloc –](../c-runtime-library/reference/malloc.md), [realloc –](../c-runtime-library/reference/realloc.md), a [volné](../c-runtime-library/reference/free.md) ke správě bloky paměti umožňující změnu velikosti v haldě.  
  
> [!IMPORTANT]
>  Kombinování **nové** a **odstranit** operátory s funkcí s možností změny velikosti přidělení paměti na stejný blok paměti bude mít za následek poškozená paměti v ladicí verze knihovny MFC. Neměli byste používat `realloc` na blok paměti přidělené s **nové**. Stejně tak by neměl přidělit paměť blok s **nové** operátor a odstranit ji s **volné**, nebo použijte **odstranit** operátor na blok paměti přidělené s `malloc`.  
  
## <a name="see-also"></a>Viz také  
 [Správa paměti: Přidělení haldy](../mfc/memory-management-heap-allocation.md)

