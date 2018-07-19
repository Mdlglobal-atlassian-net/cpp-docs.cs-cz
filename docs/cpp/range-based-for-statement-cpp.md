---
title: Range-based for Statement (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1284e4f6e096ab8021c597b841a8e983673561bd
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947628"
---
# <a name="range-based-for-statement-c"></a>Příkaz For založený na rozsahu (C++)
Vykoná příkaz `statement` opakovaně a sekvenčně pro každý prvek výrazu `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
for ( for-range-declaration : expression )  
   statement   
```  
  
## <a name="remarks"></a>Poznámky  
 Použít rozsahový **pro** příkaz k vytvoření smyček, které jsou vykonány skrze "rozsah", který je definován jako cokoli, co lze iterovat – například `std::vector`, nebo všechny ostatní standardní knihovny C++ pořadí rozsahem je definován `begin()` a `end()`. Název, který je deklarován v `for-range-declaration` je lokální pro **pro** příkazu a nemůže být předeklarováno ve `expression` nebo `statement`. Všimněte si, že [automaticky](../cpp/auto-cpp.md) je preferováno klíčové slovo `for-range-declaration` část příkazu. 

 **Novinka v sadě Visual Studio 2017:** Range-based pro smyčky už nevyžadují, aby begin() a end() vrací objekty stejného typu. To umožňuje end() vrátí objekt sentinel, například používané rozsahy, jak je definováno v návrhu rozsahy V3. Další informace najdete v tématu [zobecňuje Range-Based pro smyčky](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html) a [knihovny rozsah v3 na Githubu](https://github.com/ericniebler/range-v3).
  
 Tento kód ukazuje, jak použít rozsahový **pro** smyčky pro iteraci polem a vektorem:  
  
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

```Output
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 1 2 3 4 5 6 7 8 9 10  
  
 `end of integer array test`  
  
 `0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159`  
  
 `end of vector test`  
```

 Range-based **pro** smyčky skončí, když jeden z těchto `statement` provádí: [přerušení](../cpp/break-statement-cpp.md), [vrátit](../cpp/return-statement-cpp.md), nebo [goto](../cpp/goto-statement-cpp.md) k s popiskem příkaz mimo rozsahový **pro** smyčky. A [pokračovat](../cpp/continue-statement-cpp.md) příkaz v možnosti range-based **pro** smyčku ukončí pouze aktuální iteraci.  
  
 Mějte na paměti tyto skutečnosti o založený na rozsahu **pro**:  
  
-   Automaticky rozpozná pole.  
  
-   Rozpozná kontejnery, které mají `.begin()` a `.end()`.  
  
-   Pro vše ostatní používá vyhledávání závislé na argumentu `begin()` a `end()`.  
  
## <a name="see-also"></a>Viz také  
 [Automaticky](../cpp/auto-cpp.md)   
 [Příkazy iterace](../cpp/iteration-statements-cpp.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [while – příkaz (C++)](../cpp/while-statement-cpp.md)   
 [Proveďte-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)   
 [for – příkaz (C++)](../cpp/for-statement-cpp.md)