---
title: Podpora ladění iterátorů
ms.date: 09/13/2018
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
ms.openlocfilehash: 3ccb618c9a3c6b21d6ffe3fbbce7b6c1140e0564
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450593"
---
# <a name="debug-iterator-support"></a>Podpora ladění iterátorů

Běhová C++ Knihovna Visual runtime detekuje nesprávné použití iterátoru a vyhodnotí a zobrazí dialogové okno za běhu. Chcete-li povolit podporu iterátoru ladění, je nutné použít ladicí C++ verze standardní knihovny a běhové knihovny jazyka C pro zkompilování programu. Další informace najdete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md). Informace o tom, jak používat kontrolované iterátory, najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

C++ Standard popisuje, jak mohou členské funkce způsobit, že iterátory do kontejneru nebudou platné. Existují dva příklady:

- Mazání elementu z kontejneru způsobí, že iterátory elementu se stanou neplatnými.

- Zvětšení velikosti vektoru pomocí [](../standard-library/vector.md) operace push nebo INSERT způsobí, že `vector` iterátory se stanou neplatnými.

## <a name="invalid-iterators"></a>Neplatné iterátory

Pokud kompilujete tento ukázkový program v režimu ladění, v době běhu, který vystavuje a ukončí.

```cpp
// iterator_debugging_0.cpp
// compile by using /EHsc /MDd
#include <vector>
#include <iostream>

int main() {
   std::vector<int> v {10, 15, 20};
   std::vector<int>::iterator i = v.begin();
   ++i;

   std::vector<int>::iterator j = v.end();
   --j;

   std::cout << *j << '\n';

   v.insert(i,25);

   std::cout << *j << '\n'; // Using an old iterator after an insert
}
```

## <a name="using-iteratordebuglevel"></a>Použití _ITERATOR_DEBUG_LEVEL

Pomocí makra preprocesoru [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) můžete vypnout funkci iterátoru ladění v sestavení ladění. Tento program neuplatňuje, ale stále spouští nedefinované chování.

```cpp
// iterator_debugging_1.cpp
// compile by using: /EHsc /MDd
#define _ITERATOR_DEBUG_LEVEL 0
#include <vector>
#include <iostream>

int main() {
    std::vector<int> v {10, 15, 20};

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

## <a name="unitialized-iterators"></a>Unitialized iterátory

K vyhodnocení dojde také v případě, že se pokusíte použít iterátor před inicializací, jak je znázorněno zde:

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

## <a name="incompatible-iterators"></a>Nekompatibilní iterátory

Následující příklad kódu vyvolá kontrolní výraz, protože dva iterátory k [for_each](../standard-library/algorithm-functions.md#for_each) algoritmu jsou nekompatibilní. Zkontrolujte algoritmy a určete, zda iterátory, které jsou dodány, odkazují na stejný kontejner.

```cpp
// iterator_debugging_3.cpp
// compile by using /EHsc /MDd
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    vector<int> v1 {10, 20};
    vector<int> v2 {10, 20};

    // The next line asserts because v1 and v2 are
    // incompatible.
    for_each(v1.begin(), v2.end(), [] (int& elem) { elem *= 2; } );
}
```

Všimněte si, že tento příklad používá výraz `[] (int& elem) { elem *= 2; }` lambda namísto funktor. I když tato volba nemá žádný vliv na chybu kontrolního výrazu – podobný funktor by způsobil stejné selhání – výrazy lambda představují velmi užitečný způsob, jak provádět úlohy kompaktních objektů funkce. Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../cpp/lambda-expressions-in-cpp.md).

## <a name="iterators-going-out-of-scope"></a>Iterátory vycházející z rozsahu

K ladění kontrol iterátoru také způsobí, že proměnná iterátoru, která je deklarována ve smyčce **for** , je mimo rozsah, když končí rozsah smyčky **for** .

```cpp
// iterator_debugging_4.cpp
// compile by using: /EHsc /MDd
#include <vector>
#include <iostream>
int main() {
   std::vector<int> v {10, 15, 20};

   for (std::vector<int>::iterator i = v.begin(); i != v.end(); ++i)
      ;   // do nothing
   --i;   // C2065
}
```

## <a name="destructors-for-debug-iterators"></a>Destruktory pro iterátory ladění

Iterátory ladění mají netriviální destruktory. Pokud se destruktor nespustí, ale paměť objektu je uvolněna, může dojít k narušením přístupu a poškození dat. Vezměte v úvahu tento příklad:

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

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)
