---
title: "Podpora ladění iterátorů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- C++ Standard Library, debug iterator support
- iterators, debug iterator support
- iterators, incompatible
- incompatible iterators
- debug iterator support
ms.assetid: f3f5bd15-4be8-4d64-a4d0-8bc0761c68b6
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c0c2f0153d216292169b72e3e75d5d40fb5f35cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="debug-iterator-support"></a>Podpora ladění iterátorů
Běhové knihovny jazyka Visual C++ zjistí nesprávné iterator použití nepodmíněných výrazů a zobrazí dialogové okno v době běhu. Povolit – podpora ladění iterátorů, musíte použít ladicí verze standardní knihovny C++ a běhové knihovny jazyka C zkompilovat vašeho programu. Další informace najdete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md). Informace o tom, jak používat checked – iterátory najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).  
  
 Standardní C++ popisuje, jak členské funkce může způsobit iterátory kontejner ztratí platnost. Jsou dva příklady:  
  
-   Vymazání element z kontejneru způsobí, že iterátory do elementu ztratí platnost.  
  
-   Zvětšení velikosti [vektoru](../standard-library/vector.md) pomocí nabízené nebo vložit příčiny iterátory do `vector` ztratí platnost.  
  
## <a name="example"></a>Příklad  
Pokud zkompilujete tento ukázkový program v režimu ladění, v době běhu je vyhodnotí a ukončí.  
  
```cpp  
// iterator_debugging_0.cpp  
// compile by using /EHsc /MDd  
#include <vector>  
#include <iostream>  
  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   std::vector<int>::iterator i = v.begin();  
   ++i;  
  
   std::vector<int>::iterator j = v.end();  
   --j;  
  
   std::cout << *j << '\n';  
  
   v.insert(i,25);   
  
   std::cout << *j << '\n'; // Using an old iterator after an insert  
}  
```  
  
## <a name="example"></a>Příklad  
Můžete použít makro preprocesoru [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) vypnout iterator ladění funkce v sestavení ladicí verze. Tento program není assert, ale stále aktivuje nedefinované chování.  
  
```cpp  
// iterator_debugging_1.cpp  
// compile by using: /EHsc /MDd  
#define _ITERATOR_DEBUG_LEVEL 0  
#include <vector>  
#include <iostream>  
  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   std::vector<int>::iterator i = v.begin();  
   ++i;  
  
   std::vector<int>::iterator j = v.end();  
   --j;  
  
   std::cout << *j << '\n';  
  
   v.insert(i,25);   
  
   std::cout << *j << '\n'; // Using an old iterator after an insert  
}  
```  
  
```Output  
20  
-572662307  
```  
  
## <a name="example"></a>Příklad  
Assert dojde, pokud se pokusíte pomocí iterace před inicializací, jak je vidět tady:  
  
```cpp  
// iterator_debugging_2.cpp  
// compile by using: /EHsc /MDd  
#include <string>  
using namespace std;  
  
int main() {  
   string::iterator i1, i2;  
   if (i1 == i2)  
      ;  
}  
```  
  
## <a name="example"></a>Příklad  
Následující příklad kódu způsobí kontrolní výrazy, protože dva iterátory k [for_each –](../standard-library/algorithm-functions.md#for_each) algoritmus nejsou kompatibilní. Algoritmy zkontrolujte, zda iterátory zadaných na ně odkazovat na stejném kontejneru.  
  
```cpp  
// iterator_debugging_3.cpp  
// compile by using /EHsc /MDd  
#include <algorithm>  
#include <vector>  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int> v2;  
  
    v1.push_back(10);  
    v1.push_back(20);  
  
    v2.push_back(10);  
    v2.push_back(20);  
  
    // The next line asserts because v1 and v2 are  
    // incompatible.  
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );  
}  
```  
  
Všimněte si, že tento příklad používá výrazu lambda `[] (int& elem) { elem *= 2; }` místo functor. I když tato volba nemá žádný vliv na selhání assert – podobné functor by způsobily selhání stejné – lambdas jsou velmi užitečné způsob, jak provést compact funkce objektu úlohy. Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="example"></a>Příklad  
Ladění iterátorů kontroly také způsobit na iterator proměnnou, která je definována v `for` smyčky být mimo obor, kdy `for` cykly koncích obor.  
  
```cpp  
// iterator_debugging_4.cpp  
// compile by using: /EHsc /MDd  
#include <vector>  
#include <iostream>  
int main() {  
   std::vector<int> v ;  
  
   v.push_back(10);  
   v.push_back(15);  
   v.push_back(20);  
  
   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)  
      ;   // do nothing  
   --i;   // C2065  
}  
```  
  
## <a name="example"></a>Příklad  
Ladění iterátory mít netriviální destruktory. Pokud destruktor nespustí, bude z jakéhokoli důvodu může dojít k narušení přístupu a poškození dat. Vezměte v úvahu v tomto příkladu:  
  
```cpp  
// iterator_debugging_5.cpp  
// compile by using: /EHsc /MDd  
#include <vector>  
struct base {  
   // TO FIX: uncomment the next line  
   // virtual ~base() {}  
};  
  
struct derived : base {  
   std::vector<int>::iterator m_iter;  
   derived( std::vector<int>::iterator iter ) : m_iter( iter ) {}  
   ~derived() {}  
};  
  
int main() {  
   std::vector<int> vect( 10 );  
   base * pb = new derived( vect.begin() );  
   delete pb;  // doesn't call ~derived()  
   // access violation  
}  
```  
  
## <a name="see-also"></a>Viz také  
[Přehled knihovny C++ Standard](../standard-library/cpp-standard-library-overview.md)




