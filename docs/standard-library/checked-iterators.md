---
title: Zaškrtnutí iterátory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _SECURE_SCL_THROWS
dev_langs:
- C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 335fecb1104a3aa1754f0267eb7b9686446782ec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="checked-iterators"></a>Checked – iterátory

Kontrolované iterátory zajistí, že hranice vašeho kontejneru nebudou přepsány. Checked – iterátory vztahovat na sestavení pro vydání i ladění sestavení. Další informace o tom, jak používat iterátory ladění při kompilaci v režimu ladění najdete v tématu [podpora ladění iterátorů](../standard-library/debug-iterator-support.md).

## <a name="remarks"></a>Poznámky

Informace o tom, jak zakázat upozornění, které jsou generovány nástrojem checked – iterátory najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

Můžete použít [ \_ITERATOR\_ladění\_úroveň](../standard-library/iterator-debug-level.md) makro preprocesoru chcete povolit nebo zakázat funkci checked – iterátory. Pokud `_ITERATOR_DEBUG_LEVEL` je definován jako 1 nebo 2, unsafe použití iterátory způsobí, že chyba za běhu a program je ukončen. Pokud je definováno jako 0, jsou kontrolované iterátory zakázány. Ve výchozím nastavení, hodnota `_ITERATOR_DEBUG_LEVEL` je 0 pro verze sestavení a 2 pro ladění.

> [!IMPORTANT]
> Starší dokumentaci a zdrojový kód mohou odkazovat na [_SECURE_SCL](../standard-library/secure-scl.md) makro. Použití `_ITERATOR_DEBUG_LEVEL` na ovládací prvek `_SECURE_SCL`. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

Když `_ITERATOR_DEBUG_LEVEL` je definován jako 1 nebo 2, tyto iterator ověřování:

- Všechny standardní iterátory (například [vector::iterator](../standard-library/vector-class.md#iterator)) jsou zaškrtnutá políčka.

- Pokud výstupu iterator zaškrtnutý iterátor, volání funkce standardní knihovny, jako [std::copy](../standard-library/algorithm-functions.md#copy) zaškrtnuté chování.

- Pokud výstupu iterátor je iterátor není zaškrtnuto, způsobit volání funkce standardní knihovny upozornění kompilátoru.

- Následující funkce generovat Chyba za běhu, pokud dojde přístupu, který je mimo rozsah kontejneru:

|||||
|-|-|-|-|
|[basic_string::Operator\[\]](../standard-library/basic-string-class.md#op_at)|[bitset::Operator\[\]](../standard-library/bitset-class.md#op_at)|[zpět](../standard-library/deque-class.md#back)|[Přední](../standard-library/deque-class.md#front)|
|[deque::Operator\[\]](../standard-library/deque-class.md#op_at)|[zpět](../standard-library/list-class.md#back)|[Přední](../standard-library/list-class.md#front)|[zpět](../standard-library/queue-class.md#back)|
|[Přední](../standard-library/queue-class.md#front)|[Vector::Operator\[\]](../standard-library/vector-class.md#op_at)|[zpět](../standard-library/vector-class.md#back)|[Přední](../standard-library/vector-class.md#front)|

Když `_ITERATOR_DEBUG_LEVEL` je definován jako 0:

- Všechny standardní iterátory nezaškrtnuté. Iterátory můžete přesunout mimo hranice kontejneru, což vede k nedefinované chování.

- Pokud výstupu iterator zaškrtnutý iterátor, volání funkce standardní knihovny, jako `std::copy` zaškrtnuté chování.

- Pokud výstupu iterátor je iterátor není zaškrtnuto, volání funkce standardní knihovny získat nezaškrtnuté chování.

Zaškrtnutý iterátor odkazuje iterátor, který volá `invalid_parameter_handler` při pokusu o přesun za hranice kontejneru. Další informace o `invalid_parameter_handler`, najdete v části [ověření parametru](../c-runtime-library/parameter-validation.md).

Iterator adaptéry, které podporují checked – iterátory jsou [checked_array_iterator – třída](../standard-library/checked-array-iterator-class.md) a [unchecked_array_iterator – třída](../standard-library/unchecked-array-iterator-class.md).

## <a name="example"></a>Příklad

Když zkompilujete pomocí `_ITERATOR_DEBUG_LEVEL` nastavené na 1 nebo 2, Chyba za běhu dojde při pokusu o přístup k elementu, který je mimo rozsah kontejneru pomocí operátor indexování některých tříd.

```cpp
// checked_iterators_1.cpp
// cl.exe /Zi /MDd /EHsc /W4

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;
   v.push_back(67);

   int i = v[0];
   cout << i << endl;

   i = v[1]; //triggers invalid parameter handler
}
```

Tento program vytiskne "67" pak objeví kontrolní selhání dialogové okno s doplňujícími informacemi o selhání.

## <a name="example"></a>Příklad

Podobně když zkompilujete pomocí `_ITERATOR_DEBUG_LEVEL` nastavené na 1 nebo 2, Chyba za běhu dojde při pokusu o přístup k elementu pomocí `front` nebo `back` v třídy kontejnerů při kontejneru je prázdný.

```cpp
// checked_iterators_2.cpp
// cl.exe /Zi /MDd /EHsc /W4
#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>
#include <iostream>

using namespace std;

int main()
{
   vector<int> v;

   int& i = v.front(); // triggers invalid parameter handler
}
```

Tento program se zobrazí kontrolní selhání dialogové okno s doplňujícími informacemi o selhání.

## <a name="example"></a>Příklad

Následující kód ukazuje různé scénáře použití iterátoru s komentáři. Ve výchozím nastavení `_ITERATOR_DEBUG_LEVEL` nastavena na 2 v sestavení pro ladění a na 0 v prodejní sestavení.

```cpp
// checked_iterators_3.cpp
// cl.exe /MTd /EHsc /W4

#include <algorithm>
#include <array>
#include <iostream>
#include <iterator>
#include <numeric>
#include <string>
#include <vector>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    vector<int> v(16);
    iota(v.begin(), v.end(), 0);
    print("v: ", v);

    // OK: vector::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    vector<int> v2(16);
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });
    print("v2: ", v2);

    // OK: back_insert_iterator is marked as checked in debug mode
    // (i.e. an overrun is impossible)
    vector<int> v3;
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });
    print("v3: ", v3);

    // OK: array::iterator is checked in debug mode
    // (i.e. an overrun causes a debug assertion)
    array<int, 16> a4;
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });
    print("a4: ", a4);

    // OK: Raw arrays are checked in debug mode
    // (an overrun causes a debug assertion)
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!
    int a5[16];
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });
    print("a5: ", a5);

    // WARNING C4996: Pointers cannot be checked in debug mode
    // (an overrun causes undefined behavior)
    int a6[16];
    int * p6 = a6;
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });
    print("a6: ", a6);

    // OK: stdext::checked_array_iterator is checked in debug mode
    // (an overrun causes a debug assertion)
    int a7[16];
    int * p7 = a7;
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });
    print("a7: ", a7);

    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun causes undefined behavior)
    int a8[16];
    int * p8 = a8;
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });
    print("a8: ", a8);
}

```

Když zkompilujete tento kód pomocí `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` kompilátor vydá upozornění, ale bez chyby kompilovaný do spustitelný soubor:

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

Když se spustí na příkazovém řádku, spustitelný soubor generuje tento výstup:

```Output
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120
```

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)<br/>
