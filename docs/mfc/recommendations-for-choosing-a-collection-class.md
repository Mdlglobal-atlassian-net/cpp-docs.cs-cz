---
title: Doporučení pro výběr třídy kolekce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- type safety of collection classes [MFC]
- collection classes [MFC], serialization
- collection classes [MFC], speed
- collection classes [MFC], type safety
- collection classes [MFC], choosing
- collection classes [MFC], functionality
- shapes, collection
- collection classes [MFC], template-based
- MFC collection classes [MFC], characteristics
- collection classes [MFC], about collection classes [MFC]
- serialization [MFC], collection classes
- collection classes [MFC], duplicates allowed
- collection classes [MFC], shapes
ms.assetid: a82188cd-443f-40d8-a244-edf292a53db4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bb6338d7a40059da5f4e351dfac0d8d879e8c21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404784"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>Doporučení pro výběr třídy kolekce

Tento článek obsahuje podrobné informace, které vám pomůžou zvolit třídu kolekce pro potřeby vaší konkrétní aplikace.

Výběr třídy kolekce závisí na řadě faktorů, včetně těchto:

- Funkce obrazec třídy: pořadí, indexování a výkonu, jak je znázorněno [funkce tvar kolekce](#_core_collection_shape_features) tabulce dále v tomto tématu

- Určuje, zda třída používá šablony jazyka C++

- Určuje, zda lze serializovat prvků uložených v kolekci

- Určuje, zda může být zálohované prvků uložených v kolekci pro diagnostiku

- Určuje, zda kolekce je bezpečnost typů

V následující tabulce [funkce tvar kolekce](#_core_collection_shape_features), obsahuje souhrn vlastností obrazce k dispozici kolekce.

- Sloupce 2 a 3 popisují pořadí jednotlivých tvarů a přístup k vlastnosti. V tabulce "objednáno" se rozumí, určuje pořadí, ve kterém jsou položky vložen a odstranit jejich pořadí v kolekci. neznamená to, že jsou položky seřazeny na jejich obsah. Termín "indexované" znamená, že položka v kolekci je možné načíst podle indexu celé číslo, podobně jako položky v typické pole.

- Sloupce 4 a 5 popisují výkon jednotlivých tvarů. V aplikacích, které vyžadují mnoho vložení do kolekce rychlosti vkládání může být obzvláště důležité. u ostatních aplikací může být důležitější rychlost vyhledávání.

- Sloupec 6 popisuje, zda všechny obrazce umožňuje duplicitní prvky.

### <a name="_core_collection_shape_features"></a>  Funkce tvar kolekce

|Obrazec|Řazení|Indexované|Vkládání elementů|Hledání pro zadaný element|Duplicitní prvky|
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|
|Seznam|Ano|Ne|Rychlé|Pomalé|Ano|
|Pole|Ano|Podle int|Pomalé|Pomalé|Ano|
|Mapa|Ne|Pomocí klíče|Rychlé|Rychlé|Žádné (klíče) Ano (hodnoty)|

V následující tabulce [vlastnosti třídy kolekcí MFC](#_core_characteristics_of_mfc_collection_classes), shrnuje další důležité vlastnosti konkrétní třídy kolekcí MFC jako vodítko pro výběr. Podle vašeho výběru může záviset na, jestli je třída založené na šablonách C++, zda jeho prvky lze serializovat pomocí knihovny MFC dokumentu [serializace](../mfc/serialization-in-mfc.md) mechanismus, zda jeho elementů můžete zálohované pomocí knihovny MFC v diagnostických vypsání mechanismus, nebo Určuje, zda třída je typově bezpečný – to znamená, zda může zaručit typ prvků ukládat a načítat z kolekce na základě třídy.

### <a name="_core_characteristics_of_mfc_collection_classes"></a>  Vlastnosti třídy kolekcí MFC

|Třída|Použití jazyka C++<br /><br /> šablony|Může být<br /><br /> serializovat|Může být<br /><br /> zálohované|je<br /><br /> bezpečnost typů|
|-----------|------------------------------|---------------------------|-----------------------|-----------------------|
|`CArray`|Ano|Ano 1|Ano 1|Ne|
|`CByteArray`|Ne|Ano|Ano|Ano 3|
|`CDWordArray`|Ne|Ano|Ano|Ano 3|
|`CList`|Ano|Ano 1|Ano 1|Ne|
|`CMap`|Ano|Ano 1|Ano 1|Ne|
|`CMapPtrToPtr`|Ne|Ne|Ano|Ne|
|`CMapPtrToWord`|Ne|Ne|Ano|Ne|
|`CMapStringToOb`|Ne|Ano|Ano|Ne|
|`CMapStringToPtr`|Ne|Ne|Ano|Ne|
|`CMapStringToString`|Ne|Ano|Ano|Ano 3|
|`CMapWordToOb`|Ne|Ano|Ano|Ne|
|`CMapWordToPtr`|Ne|Ne|Ano|Ne|
|`CObArray`|Ne|Ano|Ano|Ne|
|`CObList`|Ne|Ano|Ano|Ne|
|`CPtrArray`|Ne|Ne|Ano|Ne|
|`CPtrList`|Ne|Ne|Ano|Ne|
|`CStringArray`|Ne|Ano|Ano|Ano 3|
|`CStringList`|Ne|Ano|Ano|Ano 3|
|`CTypedPtrArray`|Ano|Závisí 2|Ano|Ano|
|`CTypedPtrList`|Ano|Závisí 2|Ano|Ano|
|`CTypedPtrMap`|Ano|Závisí 2|Ano|Ano|
|`CUIntArray`|Ne|Ne|Ano|Ano 3|
|`CWordArray`|Ne|Ano|Ano|Ano 3|

1. K serializaci, musíte explicitně volat objekt kolekce `Serialize` funkce; k výpisu paměti, je třeba explicitně volat jeho `Dump` funkce. Nelze použít formuláři `ar << collObj` k serializaci nebo formuláře `dmp` `<< collObj` pro výpis.

2. Sériovost závisí na základní typ kolekce. Například, pokud je pole s typem ukazatele na základě `CObArray`, je serializovatelný; Pokud na základě `CPtrArray`, není serializovatelný. Obecně platí nemůže být serializován třídy "Ptr".

3. Pokud ano označené v tomto sloupci, objektu bez šablony třídy kolekce je typově bezpečný, používají tak, jak má. Například pokud ukládáte bajtů `CByteArray`, pole je typově bezpečné. Ale pokud ho použít k ukládání znaky, je jeho bezpečnost typů méně určité.

## <a name="see-also"></a>Viz také

[Kolekce](../mfc/collections.md)<br/>
[Třídy založené na šablonách](../mfc/template-based-classes.md)<br/>
[Postupy: Příprava typově bezpečné kolekce](../mfc/how-to-make-a-type-safe-collection.md)<br/>
[Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)

