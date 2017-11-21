---
title: "ATL – kolekce a výčty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4738e3f5256fe654dd64541dfd021ba2b4fce090
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atl-collections-and-enumerators"></a>ATL – kolekce a výčty
A `collection` je objekt modelu COM, který poskytuje rozhraní, které umožňuje přístup do skupiny datové položky (nezpracovaná data nebo jiných objektů). Rozhraní, které dodržuje standardy pro poskytování přístupu pro skupinu objektů, které se označuje jako *rozhraní kolekce*.  
  
 Minimálně musí poskytnout rozhraní pro kolekce **počet** vlastnost, která vrátí počet položek v kolekci, **položky** vlastnost, která vrací položku z kolekce založené na index a `_NewEnum` vlastnost, která vrací enumerátor pro kolekci. Volitelně můžete zadat rozhraní pro kolekce **přidat** a **odebrat** metody, které umožňují položek má být vložena do nebo odstraněn z kolekce a **zrušte** metoda odebrat všechny položky.  
  
 `enumerator` Je objekt modelu COM, který poskytuje rozhraní pro iterace v rámci položky v kolekci. Rozhraní pro výčty poskytují sériový přístup k prvků kolekce prostřednictvím čtyři metody požadované: `Next`, **přeskočit**, **resetovat**, a `Clone`.  
  
 Další informace o rozhraní pro výčty ve čtení o archetypal (ale zcela pomyslná) [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx) rozhraní.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ATL – kolekce a Enumerátor třídy](../atl/atl-collection-and-enumerator-classes.md)  
 Stručně popisuje a poskytuje odkazy na třídy ATL, které vám pomohou implementovat kolekce a výčty.  
  
 [Principy návrhu pro sběr a rozhraní pro výčty](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 Popisuje různé zásady za každý typ rozhraní.  
  
 [Implementace kolekci na základě knihovny C++ Standard](../atl/implementing-an-stl-based-collection.md)  
 Příklad rozšířené, který vás provede procesem implementace kolekce na základě standardní knihovna C++.  
  
## <a name="related-sections"></a>Související oddíly  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Obsahuje odkazy na koncepční témata o tom, jak program pomocí knihovny Active šablony.  
  
 [Ukázka ATLCollections](../visual-cpp-samples.md)  
 Ukázky, která demonstruje použití `ICollectionOnSTLImpl` a `CComEnumOnSTL`a implementace třídy zásady vlastní kopie.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)

