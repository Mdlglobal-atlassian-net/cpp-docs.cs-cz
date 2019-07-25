---
title: Checked – iterátory
ms.date: 11/04/2016
f1_keywords:
- _SECURE_SCL_THROWS
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
ms.openlocfilehash: f5a31843386d2246f5d74eae1f40b93f0ae35c90
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452129"
---
# <a name="checked-iterators"></a>Checked – iterátory

Kontrolované iterátory zajistí, že hranice vašeho kontejneru nebudou přepsány. Kontrolované iterátory platí pro sestavení vydaných verzí i pro sestavení pro ladění. Další informace o tom, jak používat iterátory ladění při kompilaci v režimu ladění, naleznete v tématu [Podpora iterátoru ladění](../standard-library/debug-iterator-support.md).

## <a name="remarks"></a>Poznámky

Informace o tom, jak zakázat upozornění, která jsou generována pomocí zkontrolovaných iterátorů, najdete v tématu [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

Pomocí makra preprocesoru [ \_na\_úrovni\_ladění iterátoru](../standard-library/iterator-debug-level.md) můžete povolit nebo zakázat funkci kontrolované iterátory. Pokud je _ITERATOR_DEBUG_LEVEL definováno jako 1 nebo 2, nezabezpečené použití iterátorů způsobí chybu za běhu a program se ukončí. Pokud je definováno jako 0, jsou kontrolované iterátory zakázány. Ve výchozím nastavení je hodnota _ITERATOR_DEBUG_LEVEL 0 pro sestavení vydaných verzí a 2 pro sestavení ladění.

> [!IMPORTANT]
> Starší dokumentace a zdrojový kód můžou odkazovat na makro [_SECURE_SCL](../standard-library/secure-scl.md) . Použijte _ITERATOR_DEBUG_LEVEL k řízení _SECURE_SCL. Další informace najdete v tématu [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

Pokud je _ITERATOR_DEBUG_LEVEL definováno jako 1 nebo 2, jsou provedeny tyto kontroly iterátoru:

- Jsou zaškrtnuty všechny standardní iterátory (například [Vector:: iterátor](../standard-library/vector-class.md#iterator)).

- Pokud je výstupní iterátor kontrolovaného iterátoru, volání do standardních funkcí knihovny, jako je například [std:: Copy](../standard-library/algorithm-functions.md#copy) Get Checked chování.

- Pokud je výstupní iterátor nekontrolované iterátor, volání funkcí standardní knihovny způsobí upozornění kompilátoru.

- Následující funkce generují běhovou chybu, pokud existuje přístup, který je mimo hranice kontejneru:

|||||
|-|-|-|-|
|[basic_string::operator\[\]](../standard-library/basic-string-class.md#op_at)|[bitset:: operator\[\]](../standard-library/bitset-class.md#op_at)|[návrat](../standard-library/deque-class.md#back)|[dopředu](../standard-library/deque-class.md#front)|
|[deque:: operator\[\]](../standard-library/deque-class.md#op_at)|[návrat](../standard-library/list-class.md#back)|[dopředu](../standard-library/list-class.md#front)|[návrat](../standard-library/queue-class.md#back)|
|[dopředu](../standard-library/queue-class.md#front)|[Vector:: – operátor\[\]](../standard-library/vector-class.md#op_at)|[návrat](../standard-library/vector-class.md#back)|[dopředu](../standard-library/vector-class.md#front)|

Když je _ITERATOR_DEBUG_LEVEL definováno jako 0:

- Všechny standardní iterátory nejsou zaškrtnuté. Iterátory lze přesunout za hranice kontejneru, což vede k nedefinovanému chování.

- Pokud je výstupní iterátor kontrolovaného iterátoru, volání funkcí standardní knihovny, jako je `std::copy` například kontrolované chování Get.

- Pokud je výstupní iterátor nezaškrtnutý iterátor, volání funkcí standardní knihovny získá nekontrolované chování.

Kontrolovaný iterátor odkazuje na iterátor, který volá `invalid_parameter_handler` , pokud se pokusíte přesunout za hranice kontejneru. Další informace o `invalid_parameter_handler`naleznete v tématu [ověření parametru](../c-runtime-library/parameter-validation.md).

Adaptér iterátoru, který podporuje kontrolované iterátory, je třídou [checked_array_iterator](../standard-library/checked-array-iterator-class.md) a [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

## <a name="example"></a>Příklad

Při kompilaci pomocí _ITERATOR_DEBUG_LEVEL nastaveného na 1 nebo 2 dojde k chybě za běhu, pokud se pokusíte o přístup k prvku, který je mimo hranice kontejneru, pomocí operátoru indexování určitých tříd.

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

Tento program vytiskne "67", čímž se zobrazí dialogové okno chyby kontrolního výrazu s dalšími informacemi o selhání.

## <a name="example"></a>Příklad

Podobně pokud kompilujete pomocí _ITERATOR_DEBUG_LEVEL nastavené na 1 nebo 2, dojde k chybě za běhu, pokud se pokusíte o přístup k prvku pomocí `front` třídy `back` nebo v kontejnerových třídách, pokud je kontejner prázdný.

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

Tento program zobrazí dialogové okno selhání kontrolního výrazu s dalšími informacemi o selhání.

## <a name="example"></a>Příklad

Následující kód ukazuje různé scénáře použití iterátoru s komentáři. Ve výchozím nastavení je _ITERATOR_DEBUG_LEVEL nastaveno na 2 v sestavení ladění a na hodnotu 0 v maloobchodních sestaveních.

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

Při kompilaci tohoto kódu pomocí `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp` kompilátoru vygeneruje upozornění, ale zkompiluje bez chyby do spustitelného souboru:

```Output
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters
that may be unsafe - this call relies on the caller to check that the passed values
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation
on how to use Visual C++ 'Checked Iterators'
```

Při spuštění z příkazového řádku vygeneruje spustitelný soubor tento výstup:

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

## <a name="see-also"></a>Viz také:

[C++Přehled standardní knihovny](../standard-library/cpp-standard-library-overview.md)\
[Podpora ladění iterátorů](../standard-library/debug-iterator-support.md)
