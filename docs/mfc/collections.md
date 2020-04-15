---
title: Kolekce
ms.date: 11/04/2016
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
ms.openlocfilehash: 3fba3a3c6cd3fecbda7f46575b1d72c450c44019
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361871"
---
# <a name="collections"></a>Kolekce

Knihovna tříd Microsoft Foundation poskytuje třídy kolekce pro správu skupin objektů. Tyto třídy jsou dvou typů:

- [Třídy kolekce vytvořené ze šablon jazyka C++](#_core_the_template_based_collection_classes)

- [Třídy kolekce, které nejsou vytvořeny ze šablon](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> Pokud váš kód již používá třídy kolekce nontemplate, můžete pokračovat v jejich použití. Pokud píšete nové třídy kolekce bezpečné ho typu pro vlastní datové typy, doporučujeme použít novější třídy založené na šabloně.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>Obrazce kolekce

Třída kolekce se vyznačuje svým "tvarem" a typy jejích prvků. Obrazec odkazuje na způsob, jakým jsou objekty uspořádány a uloženy v kolekci. Knihovna MFC poskytuje tři základní kolekce obrazců: seznamy, pole a mapy (označované také jako slovníky). Můžete vybrat obrazec kolekce, který je nejvhodnější pro konkrétní problém s programováním.

Každý ze tří zadaných obrazců kolekce je stručně popsán dále v tomto tématu. Chcete-li porovnat funkce obrazců, které vám pomohou rozhodnout, který je pro váš program nejvhodnější, naleznete [v tématu Doporučení pro výběr třídy kolekce](../mfc/recommendations-for-choosing-a-collection-class.md).

- Seznam

   Třída seznamu obsahuje seřazený, neindexovaný seznam prvků implementovaný jako dvojtečkně propojený seznam. Seznam má "hlavu" a "ocas", a přidávání nebo odstraňování prvků z hlavy nebo ocasu, nebo vkládání nebo mazání prvků ve středu, je velmi rychlý.

- Pole

   Třída pole poskytuje dynamicky dimenzované, uspořádané a celočíselné indexované pole objektů.

- Mapa (také známá jako slovník)

   Mapa je kolekce, která přidružuje klíčový objekt k objektu hodnoty.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>Třídy kolekce založené na šabloně

Nejjednodušší způsob, jak implementovat kolekci bezpečné ho typu, která obsahuje objekty libovolného typu, je použít jednu z tříd založených na šabloně knihovny MFC. Příklady těchto tříd naleznete v mfc vzorku [COLLECT](../overview/visual-cpp-samples.md).

V následující tabulce jsou uvedeny třídy kolekce založené na šablonách knihovny MFC.

### <a name="collection-template-classes"></a>Třídy šablon kolekce

|Obsah sbírky|Pole|Seznamy|Maps|
|-------------------------|------------|-----------|----------|
|Kolekce objektů libovolného typu|`CArray`|`CList`|`CMap`|
|Kolekce ukazatelů na objekty libovolného typu|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>Třídy kolekce, které nejsou založeny na šablonách

Pokud vaše aplikace již používá třídy mfc nontemplate, můžete je nadále používat. Pro nové kolekce však doporučujeme použít třídy založené na šabloně. V následující tabulce jsou uvedeny třídy kolekce knihovny MFC, které nejsou založeny na šablonách.

### <a name="nontemplate-collection-classes"></a>Třídy kolekce nešablon

|Pole|Seznamy|Maps|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Charakteristiky knihovny MFC třídy tabulky v [doporučení pro výběr kolekce třídy](../mfc/recommendations-for-choosing-a-collection-class.md) popisuje třídy kolekce knihovny MFC z hlediska těchto vlastností (jiné než tvar):

- Zda třída používá šablony Jazyka C++

- Zda prvky uložené v kolekci lze serializovat

- Zda prvky uložené v kolekci mohou být dumpingové pro diagnostiku

- Zda je kolekce typově bezpečná

### <a name="what-do-you-want-to-do"></a>Co chcete dělat

#### <a name="general-collection-class-tasks"></a>Obecné úkoly třídy kolekce

- [Doporučení pro výběr třídy kolekce](../mfc/recommendations-for-choosing-a-collection-class.md)

- [Postupy: Příprava typově bezpečné kolekce](../mfc/how-to-make-a-type-safe-collection.md)

- [Vytváření kolekcí zásobníků a front](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Přidat](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Úlohy třídy kolekce založené na šabloně

- [Třídy založené na šablonách](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Přístup k členům kolekce (na základě šablony nebo ne)

- [Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)

- [Smazání všech objektů v kolekcích CObject](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)
