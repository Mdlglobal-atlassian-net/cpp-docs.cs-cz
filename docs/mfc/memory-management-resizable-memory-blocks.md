---
title: 'Správa paměti: Paměťové bloky umožňující změnu velikosti'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: b048b60a5512ecc54750cb980ca67e2373e2c837
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364779"
---
# <a name="memory-management-resizable-memory-blocks"></a>Správa paměti: Paměťové bloky umožňující změnu velikosti

**Nové** a **odstranit** operátory, popsané v článku [Správa paměti: Příklady](../mfc/memory-management-examples.md), jsou vhodné pro přidělování a amlokaci bloky paměti pevné velikosti a objekty. V některých případě aplikace může potřebovat bloky paměti s nastavitelnou velikost. Je nutné použít standardní C run-time knihovny funkce [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)a [zdarma](../c-runtime-library/reference/free.md) pro správu bloků paměti s nastavitelnou velikostí na haldě.

> [!IMPORTANT]
> Smíchání **mandatorních** a **odstraňovacích** operátorů s funkcemi přidělení paměti s nastavitelnou platností na stejném bloku paměti bude mít za následek poškozenou paměť v ladicí verzi knihovny MFC. Neměli byste používat **realloc** na bloku paměti přidělené **s new**. Stejně tak byste neměli přidělit blok paměti s **novým** operátorem a odstranit jej s **free**, nebo použít operátor **delete** na bloku paměti přidělené **malloc**.

## <a name="see-also"></a>Viz také

[Správa paměti: Přidělení haldy](../mfc/memory-management-heap-allocation.md)
