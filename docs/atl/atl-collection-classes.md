---
title: ATL – třídy kolekce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3f26959fd7abd2ae1be945b1304370152301099
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465012"
---
# <a name="atl-collection-classes"></a>ATL – třídy kolekce
Knihovna ATL poskytuje mnoho tříd pro ukládání a přístup k datům. Které třídy rozhodnete použít závisí na několika různými faktory, včetně:  
  
-   Množství dat, který bude uložen  
  
-   Efektivita a výkon přístupu k datům  
  
-   Možnost přístupu k datům pomocí indexu nebo klíče  
  
-   Uspořádání dat  
  
-   Osobní předvoleb  
  
## <a name="small-collection-classes"></a>Malé kolekce tříd  
 Knihovna ATL poskytuje následující pole třídy pro práci s čísly objektů. Tyto třídy jsou ale omezené a určený k použití interně v knihovně ATL Nedoporučujeme, můžete použít ve svých programech.  
  
|Třída|Typ úložiště dat|  
|-----------|--------------------------|  
|[Csimplearray –](../atl/reference/csimplearray-class.md)|Implementuje třídu pole pro práci s čísly objektů.|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Implementuje třídu mapování pro práci s čísly objektů.|  
  
## <a name="general-purpose-collection-classes"></a>Obecné kolekce tříd  
 Postupujte podle třídy implementace pole, seznamy a mapy a jsou k dispozici jako obecné kolekce tříd:  
  
|Třída|Typ úložiště dat|  
|-----------|--------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|Implementuje pole.|  
|[Catllist –](../atl/reference/catllist-class.md)|Implementuje seznam.|  
|[CAtlMap](../atl/reference/catlmap-class.md)|Implementuje strukturu mapování, které data lze odkazovat pomocí klíče nebo hodnoty.|  
|[Crbmap –](../atl/reference/crbmap-class.md)|Implementuje strukturu mapování pomocí algoritmu Red Black.|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Implementuje strukturu multimapping Red Black.|  
  
 Tyto třídy bude zachytávat mnoho programovacích chyb při použití v sestavení ladění, ale pro ukazujeme výkonu, nebudou provedeny tyto kontroly v prodejní buildy.  
  
## <a name="specialized-collection-classes"></a>Specializované kolekce tříd  
 Více specializované třídy kolekcí jsou k dispozici také pro správu paměti ukazatele a interface ukazatele:  
  
|Třída|Účel|  
|-----------|-------------|  
|[Cautoptrarray –](../atl/reference/cautoptrarray-class.md)|Poskytuje metody, které jsou užitečné při vytváření pole inteligentních ukazatelů.|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Poskytuje metody, které jsou užitečné při vytváření seznamu inteligentní ukazatele.|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Úložiště `IUnknown` ukazatele a je určený jako parametr, který se použije [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) šablony třídy.|  
|[Cheapptrlist –](../atl/reference/cheapptrlist-class.md)|Poskytuje metody, které jsou užitečné při vytváření seznamu haldy ukazatele.|  
|[Cinterfacearray –](../atl/reference/cinterfacearray-class.md)|Poskytuje metody, které jsou užitečné při vytváření pole z ukazatele rozhraní modelu COM.|  
|[Cinterfacelist –](../atl/reference/cinterfacelist-class.md)|Poskytuje metody, které jsou užitečné při vytváření seznamu ukazatele rozhraní modelu COM.|  
  
## <a name="choosing-a-collection-class"></a>Výběr třídy kolekce  
 Každá z třídy kolekcí k dispozici nabízí jiné výkonové charakteristiky, jak je znázorněno v následující tabulce.  
  
-   Sloupce 2 a 3 popisují každou třídu řazení a přístup k vlastnosti. V tabulce "objednáno" se rozumí, určuje pořadí, ve kterém jsou položky vložen a odstranit jejich pořadí v kolekci. neznamená to, že jsou položky seřazeny na jejich obsah. Termín "indexované" znamená, že položka v kolekci je možné načíst podle indexu celé číslo, podobně jako položky v typické pole.  
  
-   Sloupce 4 a 5 popisují každou třídu výkonu. V aplikacích, které vyžadují mnoho vložení do kolekce rychlosti vkládání může být obzvláště důležité. u ostatních aplikací může být důležitější rychlost vyhledávání.  
  
-   Sloupec 6 popisuje, zda všechny obrazce umožňuje duplicitní prvky.  
  
-   Vztah mezi čas potřebný k dokončení operace a počet prvků v kolekci je vyjadřují výkon operace třídy dané kolekce. Operace dobu, jakou trvá, který zvyšuje lineárně popsané počtem elementů jako O(n) algoritmus. Naopak operace trvá určitou dobu, kterým se zvyšuje nižší a méně jako počtem elementů je popsaná jako algoritmus O (protokolu n). Z hlediska výkonu, proto O (protokolu n) algoritmy překonat O(n) algoritmy čím dál tím víc jako počtem elementů.  
  
### <a name="collection-shape-features"></a>Funkce tvar kolekce  
  
|Obrazec|Řazení|Indexované|Vložení<br /><br /> – element|Hledání<br /><br /> zadaný element|Duplicitní<br /><br /> elementy|  
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|  
|Seznam|Ano|Ne|Fast (konstantní čas)|Pomalé O(n)|Ano|  
|Pole|Ano|Podle int (konstantní čas)|Pomalé O(n), s výjimkou Pokud vložení na konci, v jaké velikosti písmen konstantním času|Pomalé O(n)|Ano|  
|Mapa|Ne|Klíčem (konstantní čas)|Fast (konstantní čas)|Fast (konstantní čas)|Žádné (klíče) Ano (hodnoty)|  
|Mapa Red – černá|Ano (podle klíče)|Klíčem O (protokolu n)|Rychlé O (protokolu n)|Rychlé O (protokolu n)|Ne|  
|Multimap Red – černá|Ano (podle klíče)|Klíčem O(log n) (více hodnot pro klíč)|Rychlé O (protokolu n)|Rychlé O (protokolu n)|Ano (více hodnot pro klíč)|  
  
## <a name="using-ctraits-objects"></a>Pomocí ctraits – objekty  
 Jako ATL – třídy kolekce můžete použít k ukládání širokou škálu uživatelem definované datové typy, může být užitečné mít možnost přepsat důležité funkce, jako je například porovnávání. Toho můžete dosáhnout použitím ctraits – třídy.  
  
 Ctraits – třídy jsou podobné, ale flexibilnější, než MFC kolekce tříd pomocných funkcí; Zobrazit [pomocné rutiny třídy kolekce](../mfc/reference/collection-class-helpers.md) Další informace.  
  
 Při vytváření třídy kolekce, máte možnost určení ctraits – třídy. Tato třída bude obsahovat kód, který bude provádět operace, jako je porovnání, když se zavolá pomocí jiné metody, které tvoří třídu kolekce. Pokud objekt seznam obsahuje vlastní struktury definované uživatelem, můžete chtít znovu definovat test rovnosti porovnávat pouze určité proměnné členů. Tímto způsobem bude fungovat na objektu seznamu najít metodu více vhodným způsobem.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]  
  
## <a name="comments"></a>Komentáře  
 Seznam ctraits – třídy najdete v tématu [třídy kolekcí](../atl/collection-classes.md).  
  
 Následující diagram znázorňuje hierarchii tříd pro ctraits – třídy.  
  
 ![Hierarchie osobnostní rysy pro třídy kolekce](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")  
  
## <a name="collection-classes-samples"></a>Třídy kolekcí ukázky  
 Následující ukázky ukazují třídy kolekcí:  
  
-   [Ukázka MMXSwarm](../visual-cpp-samples.md)  
  
-   [Příklad DynamicConsumer](../visual-cpp-samples.md)  
  
-   [Příklad UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)  
  
-   [Výběr ukázky](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../atl/active-template-library-atl-concepts.md)   
 [Třídy kolekce](../atl/collection-classes.md)

