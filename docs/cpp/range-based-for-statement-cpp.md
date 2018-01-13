---
title: "Na základě rozsahu pro příkaz (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 43ded324227878b44f997e6539e060145ad0fb66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="range-based-for-statement-c"></a>Příkaz For založený na rozsahu (C++)
Vykoná příkaz `statement` opakovaně a sekvenčně pro každý prvek výrazu `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      for ( for-range-declaration : expression )  
   statement   
```  
  
## <a name="remarks"></a>Poznámky  
 Použijte založený na rozsahu `for` příkaz k vytvoření smyčky, které musí být spuštěn prostřednictvím "rozsah", která je definována jako všechno, co můžete iterovat – například `std::vector`, nebo jiné pořadí standardní knihovna C++, jejichž rozsah je definované `begin()` a `end()`. Jméno, které je deklarováno v oblasti `for-range-declaration`, je lokální pro příkaz `for` a nemůže být předeklarováno ve výrazu `expression` nebo příkazu `statement`. Všimněte si, že [automaticky](../cpp/auto-cpp.md) – klíčové slovo je upřednostňováno v `for-range-declaration` část příkazu. 

 **Nové ve Visual Studio 2017:** na základě rozsahu pro smyčky už nevyžadují, aby begin() a end() vrátí objekty stejného typu. To umožňuje end() vrátit objekt sentinel, jako používá rozsahy definovaným v návrhu rozsahy V3. Další informace najdete v tématu [generalizací založený na rozsahu Smyčka For](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) a [knihovny rozsah v3 na Githubu](https://github.com/ericniebler/range-v3).
  
 Tento kód ukazuje, jak používat na základě rozsahu `for` smyčky k iteraci v rámci pole a vektor:  
  
```cpp  
// range-based-for.cpp  
// compile by using: cl /EHsc /nologo /W4  
#include <iostream>  
#include <vector>  
using namespace std;  
  
int main()   
{  
    // Basic 10-element integer array.  
    int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  
  
    // Range-based for loop to iterate through the array.  
    for( int y : x ) { // Access by value using a copy declared as a specific type.   
                       // Not preferred.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    // The auto keyword causes type inference to be used. Preferred.  
  
    for( auto y : x ) { // Copy of 'x', almost always undesirable  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( auto &y : x ) { // Type inference by reference.  
        // Observes and/or modifies in-place. Preferred when modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
  
    for( const auto &y : x ) { // Type inference by const reference.  
        // Observes in-place. Preferred when no modify is needed.  
        cout << y << " ";  
    }  
    cout << endl;  
    cout << "end of integer array test" << endl;  
    cout << endl;  
  
    // Create a vector object that contains 10 elements.  
    vector<double> v;  
    for (int i = 0; i < 10; ++i) {  
        v.push_back(i + 0.14159);  
    }  
  
    // Range-based for loop to iterate through the vector, observing in-place.  
    for( const auto &j : v ) {  
        cout << j << " ";  
    }  
    cout << endl;  
    cout << "end of vector test" << endl;  
}  
  
```  
  
 Zde je výstup:  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `1 2 3 4 5 6 7 8 9 10`  
  
 `end of integer array test`  
  
 `0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159`  
  
 `end of vector test`  
  
 Rozsah založené `for` smyčky ukončí, pokud některá z těchto `statement` se spustí: [zalomení](../cpp/break-statement-cpp.md), [vrátit](../cpp/return-statement-cpp.md), nebo [goto](../cpp/goto-statement-cpp.md) pro příkaz s popiskem mimo na základě rozsahu **pro** smyčky. A [pokračovat](../cpp/continue-statement-cpp.md) příkaz rozsah založený na `for` ukončí jenom na aktuální iteraci smyčky.  
  
 Při použití rozsahového klíčového slova `for` je třeba pamatovat na následující:  
  
-   Automaticky rozpozná pole.  
  
-   Rozpozná kontejnery, které mají `.begin()` a `.end()`.  
  
-   Pro vše ostatní používá vyhledávání závislé na argumentu `begin()` a `end()`.  
  
## <a name="see-also"></a>Viz také  
 [automaticky](../cpp/auto-cpp.md)   
 [Příkazy iterace](../cpp/iteration-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [while – příkaz (C++)](../cpp/while-statement-cpp.md)   
 [Proveďte-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)   
 [for – příkaz (C++)](../cpp/for-statement-cpp.md)