---
title: Doporučení pro výběr třídy kolekce
ms.date: 11/04/2016
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
ms.openlocfilehash: 53a4eb3e30048d9dc82722d912a026d63a87586d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371748"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>Doporučení pro výběr třídy kolekce

Tento článek obsahuje podrobné informace, které vám pomohou vybrat třídu kolekce pro vaše konkrétní potřeby aplikace.

Výběr třídy kolekce závisí na řadě faktorů, včetně:

- Funkce obrazce třídy: pořadí, indexování a výkon, jak je znázorněno v tabulce [Prvky obrazce kolekce](#_core_collection_shape_features) dále v tomto tématu

- Zda třída používá šablony Jazyka C++

- Zda prvky uložené v kolekci lze serializovat

- Zda prvky uložené v kolekci mohou být dumpingové pro diagnostiku

- Zda je kolekce typově bezpečná

Následující tabulka [Prvky obrazce kolekce](#_core_collection_shape_features)shrnuje charakteristiky dostupných obrazců kolekce.

- Sloupce 2 a 3 popisují charakteristiky pořadí a přístupu každého obrazce. V tabulce termín "objednané" znamená, že pořadí, ve kterém jsou položky vloženy a odstraněny určuje jejich pořadí v kolekci; neznamená to, že položky jsou seřazeny podle jejich obsahu. Termín "indexované" znamená, že položky v kolekci lze načíst podle celého indexu, podobně jako položky v typické pole.

- Sloupce 4 a 5 popisují výkon každého obrazce. V aplikacích, které vyžadují mnoho vložení do kolekce, může být obzvláště důležitá rychlost vkládání; pro jiné aplikace může být důležitější rychlost vyhledávání.

- Sloupec 6 popisuje, zda každý obrazec umožňuje duplicitní prvky.

### <a name="collection-shape-features"></a><a name="_core_collection_shape_features"></a>Prvky obrazce kolekce

|Obrazec|Objednáno|Indexované|Vložení prvku|Hledat zadaný prvek|Duplicitní prvky|
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|
|Seznam|Ano|Ne|Rychle|Pomalé|Ano|
|Pole|Ano|Podle int|Pomalé|Pomalé|Ano|
|Mapa|Ne|Podle klíče|Rychle|Rychle|Ne (klíče) Ano (hodnoty)|

Následující tabulka [Charakteristiky tříd kolekce knihovny MFC](#_core_characteristics_of_mfc_collection_classes)shrnuje další důležité charakteristiky konkrétních tříd kolekce knihovny MFC jako vodítko pro výběr. Vaše volba může záviset na tom, zda je třída založena na šablonách jazyka C++, zda lze její prvky serializovat pomocí mechanismu [serializace](../mfc/serialization-in-mfc.md) dokumentů knihovny MFC, zda mohou být její prvky vysazovány prostřednictvím mechanismu diagnostického dumpingu knihovny MFC nebo zda je třída typově bezpečná – to znamená, zda můžete zaručit typ prvků uložených v kolekci založené na třídě a načtené z ní.

### <a name="characteristics-of-mfc-collection-classes"></a><a name="_core_characteristics_of_mfc_collection_classes"></a>Charakteristiky tříd kolekce knihovny MFC

|Třída|Používá C++<br /><br /> šablony|Může být<br /><br /> Serializovat|Může být<br /><br /> Dumpingových|Is<br /><br /> typově bezpečné|
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
|`CTypedPtrArray`|Ano|Záleží 2|Ano|Ano|
|`CTypedPtrList`|Ano|Záleží 2|Ano|Ano|
|`CTypedPtrMap`|Ano|Záleží 2|Ano|Ano|
|`CUIntArray`|Ne|Ne|Ano|Ano 3|
|`CWordArray`|Ne|Ano|Ano|Ano 3|

1. Chcete-li serializovat, musíte explicitně volat `Serialize` funkci objektu kolekce; k výpisu, musíte `Dump` explicitně volat jeho funkci. Formulář `ar << collObj` nelze použít k serializaci nebo `dmp` `<< collObj` formulář k výpisu.

2. Serializovatelnost závisí na základní typ kolekce. Pokud je například pole zadaného `CObArray`ukazatele založeno na , je serializovatelné; pokud je `CPtrArray`založen na , není serializovatelný. Obecně platí, že třídy "Ptr" nelze serializovat.

3. Pokud je v tomto sloupci označena ano, třída kolekce bez šablony je typově bezpečná za předpokladu, že ji použijete tak, jak bylo zamýšleno. Pokud například ukládáte bajty `CByteArray`v poli , je pole bezpečné pro daný typ. Ale pokud jej používáte k ukládání znaků, jeho bezpečnost typů je méně jistá.

## <a name="see-also"></a>Viz také

[Kolekce](../mfc/collections.md)<br/>
[Třídy založené na šablonách](../mfc/template-based-classes.md)<br/>
[Postupy: Příprava typově bezpečné kolekce](../mfc/how-to-make-a-type-safe-collection.md)<br/>
[Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)
