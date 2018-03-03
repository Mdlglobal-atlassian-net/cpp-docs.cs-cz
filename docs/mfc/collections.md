---
title: Kolekce | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, collections
- arrays [MFC], classes
- MFC collection classes
- shapes, collection
- collection classes [MFC], MFC
- collections, about collections
- array templates [MFC]
- collection classes [MFC], template-based
- collection classes [MFC], about collection classes
- collection classes [MFC], maps
- collection classes [MFC], arrays
- shapes
- collection classes [MFC], lists
- collection classes [MFC], shapes
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e980f3f8fe86b621cb1494b08aec3fcdcb49f54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="collections"></a>Kolekce
Knihovny Microsoft Foundation Class poskytuje třídy kolekcí ke správě skupin objektů. Tyto třídy jsou dvou typů:  
  
-   [Třídy kolekce vytvořené z šablon C++](#_core_the_template_based_collection_classes)  
  
-   [Třídy kolekce není vytvořené z šablon](#_core_the_collection_classes_not_based_on_templates)  
  
> [!NOTE]
>  Pokud váš kód už používá třídy kolekce objektu bez šablony, můžete nadále používat. Pokud píšete nové třídy typově bezpečné kolekce pro vlastní typy dat, doporučujeme použít novější třídy na základě šablon.  
  
##  <a name="_core_collection_shapes"></a>Kolekce tvarů  
 Třídy kolekce je rozdělení, podle jeho "tvar" a typy jejích elementů. Tvar, který odkazuje na způsob objekty jsou uspořádány a uložených v kolekci. Knihovna MFC poskytuje tři základní kolekce tvarů: uvádí, polí a mapy (také označované jako slovník). Můžete si vybrat kolekci obrazec, který je nejvhodnější pro váš konkrétní programovací problém.  
  
 Každá ze tří tvarů zadané kolekci je popsána stručně později v tomto tématu. Pokud chcete porovnat funkce tvarů vám pomohou rozhodnout, která je nejvhodnější pro váš program, najdete v části [doporučení pro výběr třídy kolekce](../mfc/recommendations-for-choosing-a-collection-class.md).  
  
-   Seznam  
  
     List – třída poskytuje neindexované, seřazený seznam elementů, které jsou implementované jako dvakrát propojený seznam. Seznam obsahuje "head" a "tail" a přidávání nebo odebírání elementů z head nebo tail, nebo vložení nebo odstranění elementy uprostřed, je velmi rychle.  
  
-   Pole  
  
     Array – třída poskytuje dynamicky velikostí, seřazené a indexované celé číslo pole objektů.  
  
-   Mapy (také označované jako slovník)  
  
     Mapu je kolekce, která přidruží objekt hodnoty klíče objektu.  
  
##  <a name="_core_the_template_based_collection_classes"></a>Třídy kolekcí založených na šablonách  
 Nejjednodušší způsob, jak implementovat typově bezpečné kolekce, který obsahuje objekty libovolného typu, je použít jednu z tříd MFC na základě šablon. Příklady těchto tříd naleznete v ukázce MFC [SHROMAŽĎOVAT](../visual-cpp-samples.md).  
  
 Následující tabulka uvádí třídy MFC založených na šablonách kolekce.  
  
### <a name="collection-template-classes"></a>Šablony třídy kolekce  
  
|Obsah kolekce|Pole|Seznamy|Mapy|  
|-------------------------|------------|-----------|----------|  
|Kolekce objektů typu|`CArray`|`CList`|`CMap`|  
|Ukazatelé na objekty jakýkoli typ kolekce|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|  
  
##  <a name="_core_the_collection_classes_not_based_on_templates"></a>Třídy kolekce není založené na šablonách  
 Pokud už vaše aplikace používá MFC – třídy objektu bez šablony, můžete nadále používat. Pro nové kolekce, ale doporučujeme použít třídy na základě šablon. Následující tabulka uvádí třídy MFC kolekce, které nejsou založené na šablonách.  
  
### <a name="nontemplate-collection-classes"></a>Třídy kolekce objektu bez šablony  
  
|Pole|Seznamy|Mapy|  
|------------|-----------|----------|  
|`CObArray`|`CObList`|`CMapPtrToWord`|  
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|  
|`CDWordArray`|`CStringList`|`CMapStringToOb`|  
|`CPtrArray`||`CMapStringToPtr`|  
|`CStringArray`||`CMapStringToString`|  
|`CWordArray`||`CMapWordToOb`|  
|`CUIntArray`||`CMapWordToPtr`|  
  
 Třídy vlastností z MFC kolekce tabulky v [doporučení pro výběr třídy kolekce](../mfc/recommendations-for-choosing-a-collection-class.md) popisuje třídy MFC kolekce z hlediska tyto charakteristiky (jiné než tvar):  
  
-   Tom, zda třídu používá šablony jazyka C++  
  
-   Tom, zda lze serializovat elementy uložené v kolekci  
  
-   Jestli může být uložená v kolekci elementů zálohované pro diagnostiku  
  
-   Jestli je kolekce bezpečného typu  
  
### <a name="what-do-you-want-to-do"></a>Co chcete udělat  
  
#### <a name="general-collection-class-tasks"></a>Třídy kolekce obecné úlohy  
  
-   [Doporučení pro výběr třídy kolekce](../mfc/recommendations-for-choosing-a-collection-class.md)  
  
-   [Postupy: Příprava typově bezpečné kolekce](../mfc/how-to-make-a-type-safe-collection.md)  
  
-   [Vytváření kolekcí zásobníků a front](../mfc/creating-stack-and-queue-collections.md)  
  
-   [CArray::Add](../mfc/reference/carray-class.md#add)  
  
#### <a name="template-based-collection-class-tasks"></a>Úlohy na základě šablon třídy kolekce  
  
-   [Třídy založené na šablonách](../mfc/template-based-classes.md)  
  
#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Přístup ke členům kolekce (na základě šablon nebo ne)  
  
-   [Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)  
  
-   [Smazání všech objektů v kolekci CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)   
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

