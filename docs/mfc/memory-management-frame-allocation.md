---
title: 'Správa paměti: Přidělení rámce'
ms.date: 11/04/2016
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
ms.openlocfilehash: 1acf2ce89e18dd64c166103b59b5eb7007214efd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352122"
---
# <a name="memory-management-frame-allocation"></a>Správa paměti: Přidělení rámce

Přidělení v rámci přebírá její název ze "rámce zásobníku", který je nastaven při každém volání funkce. Rámec zásobníku je oblast paměti, která se dočasně uchovává argumenty pro funkci, stejně jako jakékoli proměnné, které jsou definovány místní funkci. Proměnné rámce jsou často nazývány "automatické" proměnné, protože kompilátor automaticky přiděluje místo pro ně.

Existují dvě klíčové vlastnosti rámec přidělení. Nejprve, při definování místní proměnné dostatek místo přiděluje podle rámce zásobníku pro uložení celé proměnné i v případě, že se o velké pole ani datové struktury. Za druhé se automaticky odstraní proměnné rámce při mizení z rozsahu:

[!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

Lokální funkce proměnné tohoto přechodu je obor se stane při ukončení funkce, ale rozsahu rámce proměnné může být menší než funkce, pokud se používají vnořených složených závorek. Toto automatické odstranění proměnné rámce je velmi důležité. V případě jednoduchého primitivní typy (například **int** nebo **bajtů**), pole nebo datových struktur, automatické odstranění jednoduše uvolní paměť používanou proměnné. Vzhledem k tomu, že má proměnná nepřejdou mimo rozsah, nelze přistupovat přesto. V případě objektů jazyka C++ ale proces automatické odstranění je o něco složitější.

Když je objekt definován jako proměnné rámce, jeho konstruktor je automaticky vyvolána v místě, kde došlo k definici. Když objekt dostane mimo rozsah, vyvolání jeho destruktoru automaticky před uvolnit paměť pro objekt. Toto automatické konstrukcí a destrukcí může být velmi užitečná, ale je nutné znát automatické volání, zejména destruktor.

Hlavní výhodou přidělování objektů na rámci je, že automaticky odebrány. Při přidělování objektů v rámci nemusíte starat o zapomenuté objekty způsobí nevracení paměti. (Podrobnosti o nevracení paměti, najdete v článku [zjištění nevracení paměti v knihovně MFC](/previous-versions/visualstudio/visual-studio-2010/c99kz476(v=vs.100)).) Přidělení rámce nevýhodou je, že rámec proměnné nelze použít mimo jejich rozsah. Dalším faktorem při výběru rámec přidělení a přidělení haldy je, že velké struktury a objekty, často je lepší použít haldy namísto zásobníku pro úložiště, protože je často omezené místo v zásobníku.

## <a name="see-also"></a>Viz také:

[Správa paměti](../mfc/memory-management.md)
