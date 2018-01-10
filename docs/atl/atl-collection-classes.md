---
title: "ATL – třídy kolekce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24b0fbdc5ab68319704fb59746862384198f232b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-collection-classes"></a>ATL – třídy kolekce
ATL poskytuje mnoho třídy pro ukládání a přístup k datům. Třídy, které se rozhodnete použít, závisí na několika různými faktory, včetně:  
  
-   Množství dat k uložení  
  
-   Efektivitu a výkon v přístupu k datům  
  
-   Schopnost přístupu k datům pomocí indexu nebo klíče  
  
-   Jak řazení dat  
  
-   Osobní preference  
  
## <a name="small-collection-classes"></a>Třídy kolekce malé  
 ATL poskytuje následující pole třídy pro práci s malý počet objektů. Ale tyto třídy jsou omezené a určený k použití interně pomocí ATL. Není doporučeno, můžete použít ve vašich aplikacích.  
  
|Třída|Typ úložiště dat|  
|-----------|--------------------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Implementuje třídu pole pro práci s malý počet objektů.|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implementuje třídu mapování pro práci s malý počet objektů.|  
  
## <a name="general-purpose-collection-classes"></a>Obecné účely – třídy kolekce  
 Postupujte podle třídy implementovat pole, seznamy a mapy a jsou dostupné jako třídy kolekce obecné účely:  
  
|Třída|Typ úložiště dat|  
|-----------|--------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|Implementuje pole.|  
|[CAtlList](../atl/reference/catllist-class.md)|Implementuje seznamu.|  
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementuje strukturu mapování, které můžete data odkazuje klíče nebo hodnoty.|  
|[CRBMap](../atl/reference/crbmap-class.md)|Implementuje strukturu mapování pomocí algoritmu Red černé.|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementuje strukturu multimapping Red černé.|  
  
 Tyto třídy bude depeše mnoho programovací chyb při použití v sestavení pro ladění, ale for sake of výkonu, nebudou provedeny tyto kontroly v prodejní sestavení.  
  
## <a name="specialized-collection-classes"></a>Specializované kolekce tříd  
 Více specializované třídy kolekcí jsou k dispozici také pro správu paměti ukazatele a ukazatele rozhraní:  
  
|Třída|Účel|  
|-----------|-------------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Poskytuje metody, které jsou užitečné při vytváření pole chytré ukazatele.|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Poskytuje metody, které jsou užitečné při sestavování seznamu chytré ukazatele.|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Úložiště `IUnknown` ukazatele a je určen k použití jako parametr, který se [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) třídy šablony.|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Poskytuje metody, které jsou užitečné při sestavování seznamu haldy ukazatele.|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Poskytuje metody, které jsou užitečné při vytváření pole ukazatele rozhraní COM.|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|Poskytuje metody, které jsou užitečné při sestavování seznamu ukazatele rozhraní COM.|  
  
## <a name="choosing-a-collection-class"></a>Výběr třídy kolekce  
 Všechny třídy k dispozici kolekce nabízí různé výkonové charakteristiky, jak je znázorněno v následující tabulce.  
  
-   Sloupce 2 a 3 popisují každou třídu řazení a přístup k vlastnosti. V tabulce termín "seřazené" znamená, že určuje pořadí, ve kterém jsou položky vložit a odstranit jejich pořadí v kolekci. neznamená to, že jsou položky seřazeny na jejich obsah. Termín "indexované" znamená, že položky v kolekci můžete načíst pomocí celé číslo indexu, podobně jako položky v typické pole.  
  
-   Sloupce 4 a 5 popisují každou třídu výkonu. V aplikacích, které vyžadují mnoho vložení do kolekce rychlosti vkládání může být obzvláště důležité. u ostatních aplikací může být důležitější rychlost vyhledávání.  
  
-   Sloupec 6 popisuje, zda každý tvar může obsahovat duplicitní prvky.  
  
-   Výkon operace třída dané kolekce se vyjadřuje jako vztah mezi čas potřebný k dokončení operace a počet elementů v kolekci. Operace trvá určenou dobu, zvyšuje lineárně jako počet elementů zvyšuje je označen jako O(n) algoritmu. Naopak operace trvá časový úsek, který zvyšuje menší a méně jako počet elementů zvyšuje označen jako algoritmus O (protokolu n). Z hlediska výkonu, tedy O (protokolu n) algoritmy překonat algoritmy O(n) více jako počet elementů zvyšuje.  
  
### <a name="collection-shape-features"></a>Funkce tvar kolekce  
  
|Obrazec|řazení|Indexované|Vložit<br /><br /> – element|Hledání<br /><br /> zadaný element|Duplicitní<br /><br /> elementy|  
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|  
|Seznam|Ano|Ne|Fast (konstantní čas)|Pomalé O(n)|Ano|  
|Pole|Ano|Podle int (konstantní čas)|Pomalé O(n) kromě Pokud vkládání na konci, do které případu konstantní čas|Pomalé O(n)|Ano|  
|mapy|Ne|Pomocí klíče (konstantní čas)|Fast (konstantní čas)|Fast (konstantní čas)|Žádné (klíče) Yes (hodnoty)|  
|Red černé mapy|Ano (pomocí klíče)|Pomocí klíče O (protokolu n)|Rychlé O (protokolu n)|Rychlé O (protokolu n)|Ne|  
|Multimap Red černé|Ano (pomocí klíče)|Pomocí klíče O(log n) (více hodnot pro klíč)|Rychlé O (protokolu n)|Rychlé O (protokolu n)|Ano (více hodnot pro klíč)|  
  
## <a name="using-ctraits-objects"></a>Pomocí ctraits – objekty  
 Jako ATL – třídy kolekce lze použít k uložení širokou škálu uživatelem definované datové typy, může být užitečné potlačit důležité funkce jako je například porovnání. Můžete toho dosáhnout pomocí ctraits – třídy.  
  
 Ctraits – třídy jsou podobné, ale flexibilnější než funkce Pomocník MFC kolekce tříd; v tématu [pomocné rutiny třídy kolekce](../mfc/reference/collection-class-helpers.md) Další informace.  
  
 Při vytváření třídě kolekce, máte možnost určení ctraits – třídy. Tato třída bude obsahovat kód, který bude provádět operace, jako je například porovnání při volání metody, které tvoří třídě kolekce. Například pokud list objekt obsahuje vlastní struktury definovaný uživatelem, můžete znovu definovat test rovnosti porovnat pouze určité proměnné členů. Tímto způsobem bude pracovat s metoda najít objekt seznamu užitečnější způsobem.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]  
  
## <a name="comments"></a>Komentáře  
 Seznam ctraits – třídy najdete v tématu [třídy kolekce](../atl/collection-classes.md).  
  
 Následující diagram znázorňuje hierarchie tříd pro ctraits – třídy.  
  
 ![Hierarchie vlastností pro třídy kolekce](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")  
  
## <a name="collection-classes-samples"></a>Ukázky třídy kolekce  
 Následující ukázky ukazují třídy kolekce:  
  
-   [Ukázka MMXSwarm](../visual-cpp-samples.md)  
  
-   [Příklad DynamicConsumer](../visual-cpp-samples.md)  
  
-   [Příklad UpdatePV](../visual-cpp-samples.md)  
  
-   [Ukázka rámeček](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)   
 [Třídy kolekce](../atl/collection-classes.md)

