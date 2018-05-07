---
title: Vytváření kolekcí zásobníků a front | Microsoft Docs
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
ms.openlocfilehash: 5545a1803675965cdea716e009ab70d2d72a31f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-stack-and-queue-collections"></a>Vytváření kolekcí zásobníků a front
Tento článek vysvětluje, jak vytvořit další datové struktury, jako například [zásobníky](#_core_stacks) a [fronty](#_core_queues), z rozhraní MFC seznam tříd. Příklady použití třídy odvozené od třídy `CList`, ale můžete použít `CList` přímo Pokud potřebujete přidat další funkce.  
  
##  <a name="_core_stacks"></a> Zásobníky  
 Protože standardní seznamu kolekce má head a koncovou část, je snadné vytvořit kolekci odvozené seznamu, která napodobuje chování last in first out zásobníku. Zásobník je jako zásobníky zásobníků v cafeteria. Zásobníky při přidávání do zásobníku, přejděte na zásobníku. Poslední zásobník přidán je první odeberou. Členské funkce kolekce seznamu `AddHead` a `RemoveHead` můžete použít k přidání a odeberte elementy konkrétně z hlavičky seznamu; nejvíc proto nedávno přidali, element je první odeberou.  
  
#### <a name="to-create-a-stack-collection"></a>Chcete-li vytvořit kolekci zásobníku  
  
1.  Odvození nové třídy seznamu jednu z existujících seznamu tříd MFC a přidejte další členské funkce pro podporu funkcí zásobníku operací.  
  
     Následující příklad ukazuje, jak přidat členské funkce Vložit elementy k zásobníku, funkce Náhled na nejvyšší element v zásobníku a nejvyšší element v zásobníku:  
  
     [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]  
  
 Všimněte si, že tento přístup poskytuje základní `CObList` třídy. Uživatele můžete volat žádný `CObList` člen fungovat, zda má smysl pro zásobník nebo ne.  
  
##  <a name="_core_queues"></a> Fronty  
 Protože standardní seznamu kolekce má head a koncovou část, je také snadno vytvořit kolekci odvozené seznamu, která napodobuje chování first-in-first-out fronty. Fronta je jako je například lidem v cafeteria. První osoba ve řádku je první ke zpracování. Jako další osoby přijde, přejde na konci řádku čekání jejich vypněte. Členské funkce kolekce seznamu `AddTail` a `RemoveHead` můžete použít k přidání a odebrání elementy konkrétně head na konec seznamu; nejvíc proto nedávno přidat, element je vždy poslední odeberou.  
  
#### <a name="to-create-a-queue-collection"></a>Chcete-li vytvořit kolekci fronty  
  
1.  Nový list – třída odvozena z jednoho z předdefinovaného seznamu tříd součástí knihovny Microsoft Foundation Class a přidejte další členské funkce pro podporu sémantika operace fronty.  
  
     Následující příklad ukazuje, jak můžete připojit členské funkce přidat element do konce fronty a získat element z začátek fronty.  
  
     [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]  
  
## <a name="see-also"></a>Viz také  
 [Kolekce](../mfc/collections.md)

