---
title: Vytváření kolekcí zásobníků a front
ms.date: 11/04/2016
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
ms.openlocfilehash: 5b3427f7bb2e46435ddf2768bcbb816f9d7e5c1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371605"
---
# <a name="creating-stack-and-queue-collections"></a>Vytváření kolekcí zásobníků a front

Tento článek vysvětluje, jak vytvořit další datové struktury, jako jsou [například zásobníky](#_core_stacks) a fronty , z tříd seznamu [knihovny](#_core_queues)MFC. Příklady používají třídy `CList`odvozené z `CList` aplikace , ale můžete je použít přímo, pokud nepotřebujete přidat funkce.

## <a name="stacks"></a><a name="_core_stacks"></a>Zásobníky

Vzhledem k tomu, že standardní seznam kolekce má hlavu a ocas, je snadné vytvořit odvozené seznam kolekce, která napodobuje chování poslední v první zásobníku. Hromádka je jako stoh táců v jídelně. Jako zásobníky jsou přidány do zásobníku, jdou na horní části zásobníku. Poslední přidaný zásobník je první, který má být odstraněn. Funkce členů kolekce `AddHead` `RemoveHead` seznamu a lze přidat a odebrat prvky konkrétně z hlavy seznamu; proto je naposledy přidaný prvek první, který má být odebrán.

#### <a name="to-create-a-stack-collection"></a>Vytvoření kolekce zásobníku

1. Odvodit novou třídu seznamu z jedné z existujících tříd seznamu knihovny MFC a přidat další členské funkce pro podporu funkcí operací zásobníku.

   Následující příklad ukazuje, jak přidat členské funkce pro nabízení prvků do zásobníku, prohlížení v horním prvku zásobníku a pop horní prvek ze zásobníku:

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Všimněte si, že `CObList` tento přístup zveřejňuje základní třídy. Uživatel může volat `CObList` libovolnou člennou funkci, ať už to dává smysl pro zásobník nebo ne.

## <a name="queues"></a><a name="_core_queues"></a>Fronty

Vzhledem k tomu, že standardní seznam kolekce má hlavu a ocas, je také snadné vytvořit odvozené seznam kolekce, která napodobuje chování fronty first-in-first-out. Fronta je jako řada lidí v jídelně. První osoba v řadě je první, která má být doručena. Jak přicházejí další lidé, jdou na konec fronty, aby počkali, až na ně přijde řada. Členská funkce `AddTail` kolekce `RemoveHead` seznamu a lze je použít k přidání a odebrání prvků konkrétně z hlavy nebo ocasu seznamu; proto je naposledy přidaný prvek vždy poslední, který má být odebrán.

#### <a name="to-create-a-queue-collection"></a>Vytvoření kolekce front

1. Odvodit novou třídu seznamu z jedné z předdefinovaných tříd seznamu, které jsou součástí knihovny tříd Microsoft Foundation, a přidat další členské funkce pro podporu sémantiky operací fronty.

   Následující příklad ukazuje, jak můžete připojit členské funkce přidat prvek na konec fronty a získat prvek z přední části fronty.

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Viz také

[Kolekce](../mfc/collections.md)
