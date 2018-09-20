---
title: Vytváření kolekcí zásobníků a front | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d050f27688d97cd3ef0352eed00f4dadb1fe6d98
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403783"
---
# <a name="creating-stack-and-queue-collections"></a>Vytváření kolekcí zásobníků a front

Tento článek vysvětluje, jak vytvořit další datové struktury, jako například [zásobníky](#_core_stacks) a [fronty](#_core_queues), z knihovny MFC seznam tříd. V příkladech se používá třídy odvozené od `CList`, ale můžete použít `CList` přímo nemusíte přidávat funkce.

##  <a name="_core_stacks"></a> Zásobníky

Protože standardní seznamu kolekce má head a koncovou část, je snadné vytvořit kolekci odvozené seznamu, která napodobuje chování last-in-first-out zásobníku. Zásobník je jako zásobník zásobníky v stravování. Jak zásobníky jsou přidány do zásobníku, dostanou nad rámec zásobníku. Poslední zásobník přidali je první, kdo se odeberou. Členské funkce kolekce seznamu `AddHead` a `RemoveHead` lze použít k přidání a odebere prvky z prvního seznamu; proto nejčastěji přidaná element je první, kdo se odeberou.

#### <a name="to-create-a-stack-collection"></a>Chcete-li vytvořit kolekci zásobníku

1. Odvodit novou třídu seznamu z jednoho z existujících seznamu tříd knihovny MFC a přidejte další členské funkce pro podporu funkcí zásobníku operací.

     Následující příklad ukazuje, jak přidat členské funkce Vložit prvky do zásobníku, náhled prvku na vrcholu zásobníku, a hlavní prvek ze zásobníku:

     [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

Všimněte si, že tento přístup poskytuje základní `CObList` třídy. Uživatel může vrstva volat všechny `CObList` členské funkce, zda má smysl pro zásobník nebo ne.

##  <a name="_core_queues"></a> fronty

Protože standardní seznamu kolekce má head a koncovou část, je také snadné vytváření odvozené seznamu kolekce, která napodobuje chování first-in-first-out fronty. Fronta je jako je například lidé v stravování. První osoby v řádku je první ke zpracování. Stejně jako vytvářet více lidí, přejdou na konci řádku čekat jejich zapnout. Členské funkce kolekce seznamu `AddTail` a `RemoveHead` lze použít k přidání a odebrání prvků z hlavní nebo konec seznamu; nejčastěji proto nedávno přidali, element je vždy poslední odeberou.

#### <a name="to-create-a-queue-collection"></a>Vytvoření kolekce fronty

1. Odvodit novou třídu seznamu z jednoho z předdefinovaného seznamu tříd, opatřeného knihovny Microsoft Foundation Class a přidejte další členské funkce pro podporu sémantiku operace fronty.

     Následující příklad ukazuje, jak můžete členské funkce přidat element do konce fronty a načíst prvek z přední části fronty připojit.

     [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>Viz také

[Kolekce](../mfc/collections.md)

