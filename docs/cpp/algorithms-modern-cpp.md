---
title: Algoritmy (moderní verze jazyka C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdd5742bb86992ce20f5a52f587c8557d46a97eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412293"
---
# <a name="algorithms-modern-c"></a>Algoritmy (moderní verze jazyka C++)
Pro moderní programování C++, doporučujeme používat algoritmy [standardní knihovna C++](../standard-library/cpp-standard-library-reference.md). Zde jsou některé důležité příklady:  
  
-   `for_each`, což je výchozí algoritmus traversal. (Také `transform` pro sémantiku není na místě.)  
  
-   `find_if`, což je výchozí algoritmus vyhledávání.  
  
-   `sort`, `lower_bound`a další výchozí řazení a vyhledávání algoritmy.  
  
 Pokud chcete zapsat Komparátor, použijte striktní `<` a používat *s názvem lambdas* při můžete.  
  
```cpp  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
```  
  
## <a name="loops"></a>Smyčky  
 Pokud je to možné, použijte na základě rozsahu `for` smyčky nebo algoritmus volání nebo obojí, místo ručně psané smyčky.`copy`, `transform`, `count_if`, `remove_if`, a jiné, jako je jsou mnohem lepší, než psané smyčky protože jejich záměru je zřejmé a jejich usnadňují psaní kódu bez chyb. Navíc mnoho standardní knihovna C++ algoritmy mají Optimalizace implementace, díky kterým efektivnější.  
  
 Místo staré C++ takto:  
  
```cpp  
for ( auto i = strings.begin(); i != strings.end(); ++i ) {  
   /* ... */  
}  
  
auto i = v.begin();  
  
for ( ; i != v.end(); ++i ) {  
  if (*i > x && *i < y) break;  
}  
```  
  
 Použijte moderní verze jazyka C++ takto:  
  
```cpp  
for_each( begin(strings), end(strings), [](string& s) {  
   // ...  
} );  
  
auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );  
```  
  
### <a name="range-based-for-loops"></a>Na základě rozsahu smyčky for  
 Rozsah základě `for` smyčka je funkce C ++ 11 jazyk není se standardní knihovna C++ algoritmem. Ale ho si zaslouží zmínky v toto pojednání o smyčky. Na základě rozsahu `for` smyčky, jsou rozšíření `for` – klíčové slovo a poskytují pohodlný a efektivní způsob, jak zápis smyčky, které provádějí iterace rozsah hodnot. Standardní knihovna C++ kontejnery, řetězce a pole jsou předem připravené pro založený na rozsahu `for` smyčky. Pokud chcete povolit toto nové syntaxe iterace pro typ vašeho definovaný uživatelem, přidejte následující podporu:  
  
-   A `begin` metodu, která vrátí iterovat na začátek strukturu a `end` metodu, která vrátí iterovat na konec strukturu.  
  
-   Podpora v iterator pro tyto metody: `operator*`, `operator!=`, a `operator++` (předponu verze).  
  
 Tyto metody může být členy nebo samostatné funkce.  
  
## <a name="random-numbers"></a>Náhodná čísla  
 Vypadalo, který staré CRT `rand()` funkce má mnoho nedostatky, které mají v length popsané v komunitě C++. V moderní verze jazyka C++, nemáte k řešení těchto nedostatků – ani máte skladová vlastní jednotně distribuované generátoru náhodných čísel, protože nejsou k dispozici ve standardní knihovně C++ nástroje pro jejich vytváření snadno a rychle, jak je znázorněno v [ \<náhodných >](../standard-library/random.md).  
  
## <a name="see-also"></a>Viz také  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)