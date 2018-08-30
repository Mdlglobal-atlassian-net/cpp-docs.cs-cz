---
title: ATL – kolekce a výčty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00265d3ce0f8ea867021500777d93991d245be47
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204810"
---
# <a name="atl-collections-and-enumerators"></a>ATL – kolekce a výčty
A `collection` je objekt modelu COM, která poskytuje rozhraní, která umožňuje přístup ke skupině položek dat (nezpracovaná data nebo jiných objektů). Rozhraní, která dodržuje standardy pro poskytnutí přístupu k skupiny objektů se označuje jako *rozhraní kolekce*.  
  
 Minimálně musíte zadat rozhraní kolekce `Count` vlastnost, která vrátí počet položek v kolekci, `Item` vlastnost, která vrátí položku z kolekce založené na index, a `_NewEnum` vlastnosti, která vrací enumerátor pro kolekci. Volitelně můžete zadat kolekci rozhraní `Add` a `Remove` metody, které umožňují položky, které chcete vložit do nebo z kolekce, odstraní a `Clear` metoda odebrat všechny položky.  
  
 `enumerator` Je objekt modelu COM, který poskytuje rozhraní pro procházení položek v kolekci. Poskytuje rozhraní pro výčty sériového přístupu k elementům kolekce pomocí čtyř požadované metody: `Next`, `Skip`, `Reset`, a `Clone`.  
  
 Přečtěte si další informace o rozhraní pro výčty v článku odkazovat na obsah, jako [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) rozhraní.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ATL – třídy kolekcí a výčtů](../atl/atl-collection-and-enumerator-classes.md)  
 Stručně popisuje a obsahuje odkazy na ATL – třídy, které vám pomůže implementovat kolekce a výčty.  
  
 [Principy návrhu rozhraní kolekce a výčtů](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 Tento článek popisuje různé zásady za každý typ rozhraní.  
  
 [Implementace kolekce založené na standardní knihovně C++](../atl/implementing-an-stl-based-collection.md)  
 Rozšířený příklad, který vás provede implementace kolekce založené na standardní knihovny C++.  
  
## <a name="related-sections"></a>Související oddíly  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovnu Active Template Library.  
  
 [Ukázka ATLCollections](../visual-cpp-samples.md)  
 Ukázka, která demonstruje použití `ICollectionOnSTLImpl` a `CComEnumOnSTL`a implementaci vlastních tříd zásad kopírování.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)

