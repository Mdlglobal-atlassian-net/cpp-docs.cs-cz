---
title: Podpora ladění iterátorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffcd69475d13277884deaf9ee114f3cd8d86516f
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601467"
---
# <a name="debug-iterator-support"></a>Podpora ladění iterátorů

Běhové knihovny jazyka Visual C++ zjistí použití nesprávné iterátoru, vyhodnotí a zobrazí dialogové okno v době běhu. Pokud chcete povolit – podpora ladění iterátorů, musíte použít ladicí verze knihovny Runtime jazyka C a standardní knihovny C++ kompilace programu. Další informace najdete v tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md). Informace o tom, jak pomocí kontrolovaných iterátorech naleznete v tématu [Checked Iterators](../standard-library/checked-iterators.md).

C++ standard popisuje, jak členské funkce může způsobit, že iterátory do kontejneru stanou neplatnými. Dva příklady jsou:

- Mazání element z kontejneru způsobí, že iterátory na prvek stanou neplatnými.

- Zvětšení velikosti [vektoru](../standard-library/vector.md) s využitím push nebo vložit iterátorů způsobí, že do `vector` stanou neplatnými.

## <a name="invalid-iterators"></a>Neplatný iterátorů

Pokud kompilujete tento ukázkový program v režimu ladění, za běhu se vyhodnotí a ukončí.

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

## <a name="using-iteratordebuglevel"></a>Pomocí _ITERATOR_DEBUG_LEVEL

Můžete použít preprocesor makro [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) vypnout iterační ladění funkcí v sestavení pro ladění. Tento program není výraz, ale stále vyvolá nedefinované chování.

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

## <a name="unitialized-iterators"></a>Neinicializovaných iterátorů

Vyhodnocení také v případě pokusu o použití iterátor před inicializací, jak je znázorněno zde:

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

Následující příklad kódu způsobí, že kontrolní výraz protože dvěma iterátory, které chcete [for_each](../standard-library/algorithm-functions.md#for_each) algoritmus jsou nekompatibilní. Algoritmy zaškrtněte, pokud chcete zjistit, zda iterátory, které jsou dodávány na ně odkazují stejný kontejner.

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

Všimněte si, že tento příklad používá výraz lambda `[] (int& elem) { elem *= 2; }` místo funktor. I když se tato možnost nemá žádný vliv na selhání assert – podobně jako funktor by způsobilo stejná chyba – výrazy lambda jsou velmi užitečný způsob, jak provádět úlohy compact funkce objektu. Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md).

## <a name="iterators-going-out-of-scope"></a>Iterátory probíhající mimo rozsah

Iterátor kontroly ladění také způsobit iterační proměnná, která je deklarována v **pro** smyčka bude z oboru, kdy **pro** oboru skončení smyčky.

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

## <a name="destructors-for-debug-iterators"></a>Destruktory pro ladění iterátorů

Ladění iterátory mají netriviální destruktory. Pokud destruktor se nespustí, ale uvolnění paměti objektu, může dojít k poškození data a narušení přístupu. Podívejte se například:

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
  auto vect = std::vector<int>(10);
  auto sink = new auto(std::begin(vect));
  ::operator delete(sink); // frees the memory without calling ~iterator()
} // access violation
```

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
