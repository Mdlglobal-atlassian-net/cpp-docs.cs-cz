---
title: 'Správa paměti: Bloky paměti umožňující změnu velikosti'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 124a2599e1523d5393fcf6255c88de0fd8cd72cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219139"
---
# <a name="memory-management-resizable-memory-blocks"></a>Správa paměti: Bloky paměti umožňující změnu velikosti

**Nové** a **odstranit** operátory popsané v článku [Správa paměti: Příklady](../mfc/memory-management-examples.md), jsou vhodné pro přidělování a rušení přidělení bloků paměti pevné velikosti a objekty. Vaše aplikace může v některých případech nutné bloky paměti umožňující změnu velikosti. Je nutné použít standardní funkce knihovny run-time jazyka C [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), a [bezplatné](../c-runtime-library/reference/free.md) ke správě bloky paměti umožňující změnu velikosti na haldě.

> [!IMPORTANT]
>  Kombinování **nové** a **odstranit** operátory s využitím functions přidělení paměti umožňující změnu velikosti ve stejném bloku paměti způsobí poškozená paměti v ladicí verzi knihovny MFC. Neměli byste používat **realloc** na blok paměti přidělené s **nové**. Podobně by neměl přidělení bloku paměti s **nové** operátor a odstraňte ho pomocí **bezplatné**, nebo použijte **odstranit** operátor na blok paměti s **malloc**.

## <a name="see-also"></a>Viz také:

[Správa paměti: Přidělení haldy](../mfc/memory-management-heap-allocation.md)
