---
title: Pole, seznamu a mapování tříd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 41dfe0b36548d87b5e0501c557e70f3cf11eea5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="array-list-and-map-classes"></a>Třídy pole, seznamu a mapy
Pro zpracování agregace dat, poskytuje knihovna tříd skupinu typu tříd kolekce – polí, seznamy a mapy, které mohou být uloženy různé objektu a předdefinovaných typů. Kolekce jsou dynamicky velikost. Tyto třídy lze v žádné program zapsán pro Windows, nebo ne. Jsou však velmi užitečné pro implementaci datové struktury, které definují vaší třídy dokumentů v rozhraní. Třídy specializované kolekce můžete snadno odvozena z nich, nebo můžete je vytvořit podle třídy šablony. Další informace o těchto přístupů, najdete v článku [kolekce](../mfc/collections.md). Seznam tříd kolekce šablony, najdete v článku [třídy šablon pro pole, seznamy a mapy](../mfc/template-classes-for-arrays-lists-and-maps.md).  
  
 Pole jsou jednorozměrné datové struktury, které jsou souvisle uložené v paměti. Vzhledem k tomu, že adresa paměti žádné daného elementu, lze vypočítat vynásobením index elementu velikostí elementu a přidávání výsledek do pole Základní adresa podporují velmi vysoká rychlost náhodného přístup. Ale pole jsou velmi náročné, pokud máte elementy vložení do pole, od celé pole posledních element vložit musí přesunout aby uvolnil prostor pro elementu, který chcete vložit. Pole můžete zvýšit nebo snížit podle potřeby.  
  
 Seznamy jsou podobné pole, ale jsou uloženy velmi odlišně. Každý prvek v seznamu součástí ukazatel na předchozí a další prvky, což dvakrát propojený seznam. Je velmi rychlé k přidání nebo odstranění položek, protože díky tomu pouze zahrnuje změnu na několik věcí. Seznam hledání však může být náročná, protože všechny hledání nutné spustit v některém z elementů end v seznamu.  
  
 Mapy související s hodnotou klíče na hodnotu data. Například klíč mapu může být řetězce a data ukazatel do seznamu. By požádejte mapy tak, abyste získali ukazatele spojené s konkrétní řetězec. Vyhledávání map jsou rychlé, protože mapy použít zatřiďovacích tabulek pro hledání klíče. Přidávání a odstraňování položek je také rychlé. Maps se často používají s další datové struktury jako pomocného indexy. MFC používá zvláštní druh mapy názvem [mapy zpráv](../mfc/mapping-messages.md) k mapování zpráv systému Windows na ukazatel na funkci obslužné rutiny pro zprávy.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

