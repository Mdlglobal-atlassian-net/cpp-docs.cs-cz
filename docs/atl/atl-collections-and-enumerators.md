---
title: ATL – kolekce a výčty
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 502bedb1773dc2a6edbd6679d50e9c5946228283
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491901"
---
# <a name="atl-collections-and-enumerators"></a>ATL – kolekce a výčty

`collection` Je objekt modelu COM, který poskytuje rozhraní, které umožňuje přístup ke skupině datových položek (nezpracovaná data nebo jiné objekty). Rozhraní, které následuje za standardy pro poskytnutí přístupu ke skupině objektů, se označuje jako *rozhraní kolekce*.

Přinejmenším musí rozhraní kolekce poskytovat `Count` vlastnost, která vrací počet položek v kolekci `Item` , vlastnost, která vrátí položku z kolekce na základě indexu, a `_NewEnum` vlastnost, která vrátí enumerátor pro kolekci Rozhraní kolekce mohou volitelně poskytovat `Add` a `Remove` metody, aby bylo možné vkládat položky do kolekce nebo z ní `Clear` odstraňovat, a metodu pro odebrání všech položek.

`enumerator` Je objekt modelu COM, který poskytuje rozhraní pro iteraci přes položky v kolekci. Rozhraní enumerátorů poskytují sériový přístup k prvkům kolekce prostřednictvím čtyř požadovaných metod `Next`:, `Skip`, `Reset` `Clone`a.

Další informace o rozhraních enumerátoru si můžete přečíst v tématu referenční obsah, jako je například [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) Interface.

## <a name="in-this-section"></a>V tomto oddílu

[ATL – třídy kolekcí a výčtů](../atl/atl-collection-and-enumerator-classes.md)<br/>
Stručně popisuje a poskytuje odkazy na třídy ATL, které vám pomůžou implementovat kolekce a enumerátory.

[Principy návrhu rozhraní kolekce a výčtů](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
Popisuje různé principy návrhu za každým typem rozhraní.

[Implementace kolekce založené na standardní knihovně C++](../atl/implementing-an-stl-based-collection.md)<br/>
Rozšířený příklad, který vás provede implementací C++ standardní kolekce založené na knihovně.

## <a name="related-sections"></a>Související oddíly

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovny Active Template Library.

[Ukázka ATLCollections](../overview/visual-cpp-samples.md)<br/>
Ukázka, která demonstruje použití `ICollectionOnSTLImpl` a `CComEnumOnSTL`a implementaci vlastních tříd zásad kopírování.

## <a name="see-also"></a>Viz také:

[Charakteristiky](../atl/active-template-library-atl-concepts.md)
