---
title: Kolekce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72bae0d985c81478321109c3c02c07e6b1386028
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069903"
---
# <a name="collections"></a>Kolekce

Knihovny Microsoft Foundation Class poskytuje třídy kolekcí ke správě skupin objektů. Tyto třídy jsou dvou typů:

- [Třídy kolekcí vytvořené ze šablon jazyka C++](#_core_the_template_based_collection_classes)

- [Nebyl vytvořen z šablony třídy kolekce](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
>  Pokud váš kód používá už objektu bez šablony třídy kolekcí, můžete pokračovat k jejich použití. Pokud píšete nový typově bezpečné kolekce tříd pro vlastní datové typy, doporučujeme použít novější třídy založené na šabloně.

##  <a name="_core_collection_shapes"></a> Kolekce obrazce

Třídy kolekce je charakterizovaná chyba tak, že jeho "tvar" a typy z jeho prvků. Tvar odkazuje na způsob, jak objekty jsou uspořádané a uložených v kolekci. Knihovna MFC poskytuje tři základní kolekci tvarů: seznam, pole a mapy (označované také jako slovníky). Můžete vybrat kolekci tvar, který je nejvhodnější pro váš konkrétní programovací problém.

Každá ze tří tvarů zadané kolekci je popsána stručně dále v tomto tématu. Porovnejte funkce tvary, které vám pomohou rozhodnout, která je nejvhodnější pro aplikace, najdete v článku [doporučení pro výběr třídy kolekce](../mfc/recommendations-for-choosing-a-collection-class.md).

- Seznam

   Třídy seznamu poskytuje seřazený, neindexované seznam prvků, které jsou implementovány jako dvakrát propojený seznam. Seznam obsahuje "hlavní" a "funkce tail" a přidávání nebo odebírání elementů z hlavní nebo funkce tail, nebo vložení nebo odstranění prvků uprostřed, je velmi rychlá.

- Pole

   Třídy pole obsahuje dynamicky velikosti, seřazený a indexovat celé číslo pole objektů.

- Mapa (označované také jako slovník)

   Kolekce, která přidruží objekt hodnoty klíče objektu, je objekt map.

##  <a name="_core_the_template_based_collection_classes"></a> Třídy kolekce založené na šablonách

Nejjednodušší způsob, jak implementovat typově bezpečné kolekce, která obsahuje objekty z libovolného typu je použití jedné ze tříd knihovny MFC založené na šabloně. Příklady těchto tříd, najdete v ukázce MFC [SHROMAŽĎOVAT](../visual-cpp-samples.md).

MFC – třídy kolekce založené na šablonách naleznete v následující tabulce.

### <a name="collection-template-classes"></a>Šablona třídy kolekce

|Obsah kolekce|Pole|Seznamy|Mapy|
|-------------------------|------------|-----------|----------|
|Kolekce objektů libovolného typu|`CArray`|`CList`|`CMap`|
|Kolekce ukazatelů na objekty typu|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

##  <a name="_core_the_collection_classes_not_based_on_templates"></a> Třídy kolekcí není založené na šablonách

Pokud už vaše aplikace používá třídy knihovny MFC objektu bez šablony, můžete pokračovat k jejich použití. Pro nové kolekce, ale doporučujeme použít třídy založené na šabloně. V následující tabulce jsou uvedeny třídy kolekcí MFC, které nejsou založené na šablonách.

### <a name="nontemplate-collection-classes"></a>Třídy kolekcí objektu bez šablony

|Pole|Seznamy|Mapy|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Vlastnosti z třídy kolekcí MFC tabulku v [doporučení pro výběr třídy kolekce](../mfc/recommendations-for-choosing-a-collection-class.md) popisuje třídy kolekcí MFC z hlediska tyto vlastnosti (jiné než tvar):

- Určuje, zda třída používá šablony jazyka C++

- Určuje, zda lze serializovat prvků uložených v kolekci

- Určuje, zda může být zálohované prvků uložených v kolekci pro diagnostiku

- Určuje, zda kolekce je bezpečnost typů

### <a name="what-do-you-want-to-do"></a>Co chcete udělat

#### <a name="general-collection-class-tasks"></a>Obecné třídy kolekce úloh

- [Doporučení pro výběr třídy kolekce](../mfc/recommendations-for-choosing-a-collection-class.md)

- [Postupy: Příprava typově bezpečné kolekce](../mfc/how-to-make-a-type-safe-collection.md)

- [Vytváření kolekcí zásobníků a front](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Add](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Úlohy založené na šablonách třídy kolekce

- [Třídy založené na šablonách](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Přístup k členům kolekce (založené na šablonách nebo ne)

- [Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)

- [Smazání všech objektů v kolekci CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)

