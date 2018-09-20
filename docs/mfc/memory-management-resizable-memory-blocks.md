---
title: 'Správa paměti: Paměťové bloky umožňující změnu | Dokumentace Microsoftu'
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
ms.openlocfilehash: 92582e4255c88b9cc78368a635b27772f2e51a30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443901"
---
# <a name="memory-management-resizable-memory-blocks"></a>Správa paměti: Paměťové bloky umožňující změnu velikosti

**Nové** a **odstranit** operátory popsané v článku [Správa paměti: Příklady](../mfc/memory-management-examples.md), jsou vhodné pro přidělování a rušení přidělení bloků paměti pevné velikosti a objekty. Vaše aplikace může v některých případech nutné bloky paměti umožňující změnu velikosti. Je nutné použít standardní funkce knihovny run-time jazyka C [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), a [bezplatné](../c-runtime-library/reference/free.md) ke správě bloky paměti umožňující změnu velikosti na haldě.

> [!IMPORTANT]
>  Kombinování **nové** a **odstranit** operátory s využitím functions přidělení paměti umožňující změnu velikosti ve stejném bloku paměti způsobí poškozená paměti v ladicí verzi knihovny MFC. Neměli byste používat **realloc** na blok paměti přidělené s **nové**. Podobně by neměl přidělení bloku paměti s **nové** operátor a odstraňte ho pomocí **bezplatné**, nebo použijte **odstranit** operátor na blok paměti s **malloc**.

## <a name="see-also"></a>Viz také

[Správa paměti: Přidělení haldy](../mfc/memory-management-heap-allocation.md)

