---
title: tuple_element – třída
ms.date: 11/04/2016
f1_keywords:
- utility/std::tuple_element
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
ms.openlocfilehash: 21efed39fdaabe0f95f83e9dc5cdfcc508a147c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684464"
---
# <a name="tuple_element-class"></a>tuple_element – třída

Zabalí `tuple` element. Specializace zalomí `array` prvky a `pair` prvky.

## <a name="syntax"></a>Syntaxe

```cpp
// CLASS tuple_element (find element by index)
template <size_t Index, class Tuple>
   struct tuple_element;

// tuple_element for const
template <size_t Index, class Tuple>
   struct tuple_element<Index, const Tuple>;

// tuple_element for volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, volatile Tuple>;

// tuple_element for const volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, const volatile Tuple>;

// Helper typedef
template <size_t Index, class Tuple>
   using tuple_element_t = typename tuple_element<Index, Tuple>::type;

// Specialization for arrays
template <size_t Index, class Elem, size_t Size>
   struct tuple_element<Index, array<Elem, Size>>;

// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```

### <a name="parameters"></a>Parametry

@No__t_1 *indexu*
Index určeného elementu.

@No__t_1 *řazené kolekce členů*
Typ řazené kolekce členů.

*Elem* \
Typ elementu pole.

*Velikost* \
Velikost pole.

@No__t_1 *T1*
Typ prvního prvku v páru.

*T2* \
Typ druhého prvku v páru.

## <a name="remarks"></a>Poznámky

Šablona třídy `tuple_element` má vnořenou `type` typu typedef, která je synonymem pro typ s *indexem* indexu řazené kolekce *členů*typu řazené kolekce členů.

@No__t_0 typedef je pohodlný alias pro `tuple_element<Index, Tuple>::type`.

Specializace šablony třídy pro pole poskytuje rozhraní `array` jako řazené kolekce členů `Size` prvků, z nichž každý má stejný typ. Každá specializace má vnořenou `type` typedef, která je synonymem pro typ elementu *indexu* `array`, s případnými const-volatile.

Specializace šablony pro `pair` typy poskytují jeden člen typedef, `type`, což je synonymum pro typ elementu na zadané pozici ve páru, se zachovanými const a/nebo nestálou kvalifikací. @No__t_0 typedef je pohodlný alias pro `tuple_element<N, pair<T1, T2>>::type`.

Použijte [funkci get &lt;utility &gt;](../standard-library/utility-functions.md#get) k vrácení prvku na zadané pozici nebo zadaného typu.

## <a name="example"></a>Příklad

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;
typedef tuple<int, double, string> MyTuple;

int main() {
    MyTuple c0{ 0, 1.5, "Tail" };

    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type

    cout << val << " " << val2 << " " << val3 << endl;
}
```

```Output
0 1.5 Tail
```

## <a name="example"></a>Příklad

```cpp
#include <array>
#include <iostream>

using namespace std;
typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    for (const auto& e : c0)
    {
        cout << e << " ";
    }
    cout << endl;

    // display first element "0"
    tuple_element<0, MyArray>::type val = c0.front();
    cout << val << endl;
}
```

```Output
0 1 2 3
0
```

## <a name="example"></a>Příklad

```cpp
#include <utility>
#include <iostream>

using namespace std;

typedef pair<int, double> MyPair;
int main() {
    MyPair c0(0, 1.333);

    // display contents "0 1"
    cout << get<0>(c0) << " ";
    cout << get<1>(c0) << endl;

    // display first element "0 " by index
    tuple_element<0, MyPair>::type val = get<0>(c0);
    cout << val << " ";

    // display second element by type
    tuple_element<1, MyPair>::type val2 = get<double>(c0);
    cout << val2 << endl;
}
```

```Output
0 1.333
0 1.333
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<tuple >

**Header:** \<array > (pro specializaci pole)

**Header:** \<utility > (pro specializace dvojice)

**Obor názvů:** std
