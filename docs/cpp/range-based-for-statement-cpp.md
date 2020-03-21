---
title: Příkaz For založený na rozsahu (C++)
ms.date: 11/04/2016
ms.assetid: 5750ba1d-ba48-4236-a923-e32de8345c2d
ms.openlocfilehash: af9811fd707d4dbc28158dba3b6b3fbfcc43e4fe
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077183"
---
# <a name="range-based-for-statement-c"></a>Příkaz For založený na rozsahu (C++)

Vykoná příkaz `statement` opakovaně a sekvenčně pro každý prvek výrazu `expression`.

## <a name="syntax"></a>Syntaxe

```
for ( for-range-declaration : expression )
   statement
```

## <a name="remarks"></a>Poznámky

Použijte příkaz **pro** rozsah založený na rozsahu k vytvoření smyček, které musí být provedeny prostřednictvím "rozsahu", který je definován jako cokoli, co lze iterovat, například `std::vector`nebo jakékoli jiné C++ standardní knihovny, jejichž rozsah je definován `begin()` a `end()`. Název deklarovaný v `for-range-declaration` èásti je místní pro příkaz **for** a nemůže být znovu deklarován v `expression` nebo `statement`. Všimněte si, že klíčové slovo [auto](../cpp/auto-cpp.md) je upřednostňováno v `for-range-declaration` část příkazu.

**Novinka v aplikaci Visual Studio 2017:**  Smyčky for založené na rozsahu již nevyžadují, aby objekty begin () a end () vracely stejný typ. To umožňuje, aby příkaz end () vrátil objekt Sentinel, který je používán rozsahy, jak je definováno v návrhu rozsahy-v3. Další informace najdete v tématu [generalizace smyčky for](https://wg21.link/p0184r0) a [Range-V3 Library na GitHubu](https://github.com/ericniebler/range-v3).

Tento kód ukazuje, jak použít smyčky na základě **rozsahu pro** iteraci pomocí pole a vektoru:

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

Tady je výstup:

```Output
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10
end of integer array test

0.14159 1.14159 2.14159 3.14159 4.14159 5.14159 6.14159 7.14159 8.14159 9.14159
end of vector test
```

Smyčka **na základě rozsahu** končí, když je provedena jedna z těchto `statement`: [Break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md)nebo [goto](../cpp/goto-statement-cpp.md) pro příkaz označený mimo rozsah smyčka **for** . Příkaz [Continue](../cpp/continue-statement-cpp.md) v rámci smyčky **for** končí pouze aktuální iterací.

Mějte na paměti, že tato fakta jsou založená **na rozsahu:**

- Automaticky rozpozná pole.

- Rozpozná kontejnery, které mají `.begin()` a `.end()`.

- Pro vše ostatní používá vyhledávání závislé na argumentu `begin()` a `end()`.

## <a name="see-also"></a>Viz také

[auto](../cpp/auto-cpp.md)<br/>
[Příkazy iterace](../cpp/iteration-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[while – příkaz (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for – příkaz (C++)](../cpp/for-statement-cpp.md)