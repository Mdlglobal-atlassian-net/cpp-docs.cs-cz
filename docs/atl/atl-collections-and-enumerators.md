---
title: ATL – kolekce a výčty
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: ebf7be8b2c80a714a27567ce0334475519a69454
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768013"
---
# <a name="atl-collections-and-enumerators"></a>ATL – kolekce a výčty

A `collection` je objekt modelu COM, která poskytuje rozhraní, která umožňuje přístup ke skupině položek dat (nezpracovaná data nebo jiných objektů). Rozhraní, která dodržuje standardy pro poskytnutí přístupu k skupiny objektů se označuje jako *rozhraní kolekce*.

Minimálně musíte zadat rozhraní kolekce `Count` vlastnost, která vrátí počet položek v kolekci, `Item` vlastnost, která vrátí položku z kolekce založené na index, a `_NewEnum` vlastnosti, která vrací enumerátor pro kolekci. Volitelně můžete zadat kolekci rozhraní `Add` a `Remove` metody, které umožňují položky, které chcete vložit do nebo z kolekce, odstraní a `Clear` metoda odebrat všechny položky.

`enumerator` Je objekt modelu COM, který poskytuje rozhraní pro procházení položek v kolekci. Poskytuje rozhraní pro výčty sériového přístupu k elementům kolekce pomocí čtyř požadované metody: `Next`, `Skip`, `Reset`, a `Clone`.

Přečtěte si další informace o rozhraní pro výčty v článku odkazovat na obsah, jako [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) rozhraní.

## <a name="in-this-section"></a>V tomto oddílu

[ATL – třídy kolekcí a výčtů](../atl/atl-collection-and-enumerator-classes.md)<br/>
Stručně popisuje a obsahuje odkazy na ATL – třídy, které vám pomůže implementovat kolekce a výčty.

[Principy návrhu rozhraní kolekce a výčtů](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
Tento článek popisuje různé zásady za každý typ rozhraní.

[Implementace kolekce založené na standardní knihovně C++](../atl/implementing-an-stl-based-collection.md)<br/>
Rozšířený příklad, který vás provede implementace kolekce založené na standardní knihovny C++.

## <a name="related-sections"></a>Související oddíly

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovnu Active Template Library.

[Ukázka ATLCollections](../overview/visual-cpp-samples.md)<br/>
Ukázka, která demonstruje použití `ICollectionOnSTLImpl` a `CComEnumOnSTL`a implementaci vlastních tříd zásad kopírování.

## <a name="see-also"></a>Viz také:

[Koncepty](../atl/active-template-library-atl-concepts.md)
