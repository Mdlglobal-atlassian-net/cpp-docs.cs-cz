---
title: Doporučení pro výběr třídy kolekce | Microsoft Docs
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
ms.openlocfilehash: 28527f9668b9ca6a9ef00cf399a04ce9bad65716
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353129"
---
# <a name="recommendations-for-choosing-a-collection-class"></a>Doporučení pro výběr třídy kolekce
Tento článek obsahuje podrobné informace, které vám pomohou zvolit třídu kolekce pro vaše potřeby konkrétní aplikace.  
  
 Výběr třídy kolekce závisí na počtu faktorů, včetně:  
  
-   Funkce obrazce Třída: pořadí, indexování a výkonu, jak je znázorněno v [funkce tvar kolekce](#_core_collection_shape_features) tabulce dál v tomto tématu  
  
-   Tom, zda třídu používá šablony jazyka C++  
  
-   Tom, zda lze serializovat elementy uložené v kolekci  
  
-   Jestli může být uložená v kolekci elementů zálohované pro diagnostiku  
  
-   Jestli je kolekce bezpečného typu  
  
 V následující tabulce, [funkce tvar kolekce](#_core_collection_shape_features), shrnuje charakteristiky tvarů kolekce k dispozici.  
  
-   Sloupce 2 a 3 popisují každou tvar řazení a přístup k vlastnosti. V tabulce termín "seřazené" znamená, že určuje pořadí, ve kterém jsou položky vložit a odstranit jejich pořadí v kolekci. neznamená to, že jsou položky seřazeny na jejich obsah. Termín "indexované" znamená, že položky v kolekci můžete načíst pomocí celé číslo indexu, podobně jako položky v typické pole.  
  
-   Sloupce 4 a 5 popisují každou tvar výkonu. V aplikacích, které vyžadují mnoho vložení do kolekce rychlosti vkládání může být obzvláště důležité. u ostatních aplikací může být důležitější rychlost vyhledávání.  
  
-   Sloupec 6 popisuje, zda každý tvar může obsahovat duplicitní prvky.  
  
### <a name="_core_collection_shape_features"></a>  Funkce tvar kolekce  
  
|Obrazec|řazení|Indexované|Insert – element|Vyhledejte zadaný element|Elementy s duplicitním|  
|-----------|--------------|--------------|-----------------------|----------------------------------|-------------------------|  
|Seznam|Ano|Ne|Rychlý|Pomalé|Ano|  
|Pole|Ano|Podle typu int.|Pomalé|Pomalé|Ano|  
|mapy|Ne|Pomocí klíče|Rychlý|Rychlý|Žádné (klíče) Yes (hodnoty)|  
  
 V následující tabulce, [charakteristiky z MFC – třídy kolekce](#_core_characteristics_of_mfc_collection_classes), shrnuje další důležité charakteristiky konkrétní MFC – třídy kolekce jako vodítko k výběru. Zvoleného může záviset na tom, jestli je třída podle šablonami C++, zda jeho elementy lze serializovat prostřednictvím knihovny MFC dokumentu [serializace](../mfc/serialization-in-mfc.md) mechanismus, zda může být jeho elementy zálohované prostřednictvím MFC je diagnostiky vypsání mechanismus, nebo jestli třída je bezpečnost typů – to znamená, zda může zaručit typ elementů ukládat a načítat z kolekce na základě třídy.  
  
### <a name="_core_characteristics_of_mfc_collection_classes"></a>  Charakteristické vlastnosti třídy MFC – třídy kolekce  
  
|Třída|Používá C++<br /><br /> šablony|Může být<br /><br /> serializovat|Může být<br /><br /> zálohované|je<br /><br /> bezpečnost typů|  
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
  
 1. K serializaci, musí explicitně volat objekt v kolekci `Serialize` funkce; pro výpis stavu musíte explicitně volat jeho `Dump` funkce. Nemůžete použít formuláře `ar << collObj` k serializaci nebo formuláře `dmp` `<< collObj` vypsat.  
  
 2. Sériovost závisí na nadřazený typ kolekce. Například, pokud je na základě pole typu ukazatele `CObArray`, je-li u serializovatelných; `CPtrArray`, není serializovatelný. Obecně platí nelze jej serializovat "Ptr" třídy.  
  
 3. Pokud v tomto sloupci, označení Ano, třídu kolekce objektu bez šablony je bezpečnost typů používají tak, jak má. Například, pokud uložíte bajtů `CByteArray`, pole je bezpečnost typů. Ale pokud ji použijete k uložení znaky, je jeho bezpečnost typů méně určité.  
  
## <a name="see-also"></a>Viz také  
 [Kolekce](../mfc/collections.md)   
 [Třídy založené na šablonách](../mfc/template-based-classes.md)   
 [Postupy: Příprava typově bezpečné kolekce](../mfc/how-to-make-a-type-safe-collection.md)   
 [Přístup ke všem členům kolekce](../mfc/accessing-all-members-of-a-collection.md)

