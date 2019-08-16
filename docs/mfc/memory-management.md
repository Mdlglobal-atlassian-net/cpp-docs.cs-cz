---
title: Správa paměti
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: 5d81bd0a8bdd24059951cba5c8b69751b3d1db86
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508261"
---
# <a name="memory-management"></a>Správa paměti

Tato skupina článků popisuje, jak využít služby pro obecné účely knihovna Microsoft Foundation Class (MFC) souvisejících se správou paměti. Přidělení paměti lze rozdělit do dvou hlavních kategorií: přidělení snímků a přidělení haldy.

Jedním z hlavních rozdílů mezi těmito dvěma způsoby přidělování je to, že díky alokaci snímků obvykle pracujete se skutečným blokem paměti, zatímco s přidělením haldy máte vždycky ukazatel na blok paměti. Dalším velkým rozdílem mezi těmito dvěma schématy je, že objekty rámce jsou automaticky odstraněny, zatímco objekty haldy musí být explicitně odstraněny programátorem.

Informace o správě paměti v programech pro systém Windows, které nejsou součástí knihovny MFC, najdete v tématu [Správa paměti](/windows/win32/memory/memory-management) v Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Přidělení snímků](../mfc/memory-management-frame-allocation.md)

- [Přidělení haldy](../mfc/memory-management-heap-allocation.md)

- [Přidělování paměti pro pole](../mfc/memory-management-examples.md)

- [Zrušení přidělení paměti pro pole z haldy](../mfc/memory-management-examples.md)

- [Přidělování paměti pro datovou strukturu](../mfc/memory-management-examples.md)

- [Přidělování paměti pro objekt](../mfc/memory-management-examples.md)

- [Bloky paměti umožňující změnu velikosti](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Viz také:

[Charakteristiky](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)
