---
title: Smazání všech objektů v kolekcích CObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f57e503e43bdb637b85e4642349203b9f2e8aa6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348820"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Smazání všech objektů v kolekcích CObject
Tento článek vysvětluje, jak odstranit všechny objekty v kolekci (bez odstranění samotného objektu kolekce).  
  
 Chcete-li odstranit všechny objekty v kolekci `CObject`s (nebo objektů, které jsou odvozené z `CObject`), použijte jednu z iterace technik popsaných v článku [přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md) odstranit každý objekt v Zapněte.  
  
> [!CAUTION]
>  Je možné sdílet objekty v kolekcích. To znamená kolekce udržuje ukazatel na objekt, ale ostatní součásti programu, mohou mít i ukazatele na stejný objekt. Musíte být pozor, abyste objekt, který je sdílen, dokud nebudou dokončeny všechny části, pomocí objektu.  
  
 Tento článek ukazuje, jak odstranit objekty:  
  
-   [Seznam](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)  
  
-   [Pole](#_core_to_delete_all_elements_in_an_array)  
  
-   [Mapy](#_core_to_delete_all_elements_in_a_map)  
  
#### <a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>  Chcete-li odstranit všechny objekty v seznamu ukazatelé na třídy CObject  
  
1.  Použití `GetHeadPosition` a `GetNext` k iteraci v rámci seznamu.  
  
2.  Použití **odstranit** operátor každý objekt odstranit, protože se vyskytuje v iterace.  
  
3.  Volání `RemoveAll` funkce odebrat všechny elementy ze seznamu po odstranění objekty přidružené k těmto prvkům.  
  
 Následující příklad ukazuje, jak odstranit všechny objekty ze seznamu `CPerson` objekty. Každý objekt v seznamu je ukazatel na `CPerson` objekt, který byl původně přidělené v haldě.  
  
 [!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]  
  
 Poslední volání funkce `RemoveAll`, je funkce člen seznamu, která odebere všechny elementy ze seznamu. Členská funkce `RemoveAt` odebere jeden element.  
  
 Všimněte si rozdíl mezi odstranění objektu elementu a odebrání elementu samotného. Odebrat element ze seznamu jenom odebere v seznamu odkaz na objekt. Objekt se stále existuje v paměti. Pokud odstraníte objekt, se přestanou existovat a jeho paměť je uvolnit. Proto je důležité odebrat element ihned po elementu objekt je odstraněný tak, aby při pokusu o přístup k objektům, které už existují nebude v seznamu.  
  
#### <a name="_core_to_delete_all_elements_in_an_array"></a>  Chcete-li odstranit všechny elementy v matici  
  
1.  Použití `GetSize` a celočíselné hodnoty indexu k iteraci v rámci pole.  
  
2.  Použití **odstranit** operátor odstranit každý element, jako je došlo v iteraci.  
  
3.  Volání `RemoveAll` funkce odeberte všechny elementy z pole po byla odstraněna.  
  
     Kód pro odstranění všechny elementy pole vypadá takto:  
  
     [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]  
  
 Jako příklad seznamu výše, můžete volat `RemoveAll` odebrat všechny elementy v matici nebo `RemoveAt` odebrat jednotlivý prvek.  
  
#### <a name="_core_to_delete_all_elements_in_a_map"></a> Chcete-li odstranit všechny elementy ve mapy  
  
1.  Použití `GetStartPosition` a `GetNextAssoc` k iteraci v rámci pole.  
  
2.  Použití **odstranit** operátor odstranit klíč a hodnotu pro každý element mapy, jak se vyskytuje v iterace.  
  
3.  Volání `RemoveAll` funkce k odebrání všech elementů mapy po byla odstraněna.  
  
     Kód pro odstranění všechny elementy `CMap` kolekce je následující. Každý prvek v mapě má řetězec jako klíč a `CPerson` objektu (odvozený z `CObject`) jako hodnotu.  
  
     [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]  
  
 Můžete volat `RemoveAll` odebrat všechny elementy na mapě nebo `RemoveKey` odebrat jednotlivý prvek se zadaným klíčem.  
  
## <a name="see-also"></a>Viz také  
 [Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)

