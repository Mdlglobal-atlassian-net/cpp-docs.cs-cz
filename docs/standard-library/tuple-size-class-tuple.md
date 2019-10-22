---
title: tuple_size třída;
ms.date: 11/04/2016
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
helpviewer_keywords:
- std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
ms.openlocfilehash: 361545bee020d6c3624d1d45743abcb9c2b4ac85
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688858"
---
# <a name="tuple_size-class"></a>tuple_size třída;

Oznamuje počet prvků, které `tuple` obsahuje.

## <a name="syntax"></a>Syntaxe

```cpp
// TEMPLATE STRUCT tuple_size
template <class Tuple>
   struct tuple_size;

// number of elements in array
template <class Elem, size_t Size>
   struct tuple_size<array<Elem, Size>>
      : integral_constant<size_t, Size>;

// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>>
      : integral_constant<size_t, 2>

// size of tuple
template <class... Types>
   struct tuple_size<tuple<Types...>>
      : integral_constant<size_t, sizeof...(Types)>;

// size of const tuple
template <class Tuple>
   struct tuple_size<const Tuple>;

// size of volatile tuple
template <class Tuple>
   struct tuple_size<volatile Tuple>;

// size of const volatile tuple
template <class Tuple>
   struct tuple_size<const volatile Tuple>;
```

```cpp
template <class T> inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```

### <a name="parameters"></a>Parametry

@No__t_1 *řazené kolekce členů*
Typ řazené kolekce členů.

*Elem* \
Typ prvků pole.

*Velikost* \
Velikost pole.

@No__t_1 *T1*
Typ prvního členu páru.

*T2* \
Typ druhého člena dvojice.

@No__t_1 *typů*
Typy prvků řazené kolekce členů.

## <a name="remarks"></a>Poznámky

Šablona třídy má člen `value`, který je integrální konstantní výraz, jehož hodnota je rozsah *řazené*kolekce členů typu řazené kolekce členů.

Specializace šablony pro pole má členský `value` výraz integrální konstanty, jejíž hodnota je *Size*, což je velikost pole.

Specializace šablony pro dvojici má členský `value`, který je integrálním konstantním výrazem, jehož hodnota je 2.

## <a name="example"></a>Příklad

```cpp
#include <tuple>
#include <iostream>

using namespace std;

typedef tuple<int, double, int, double> MyTuple;
int main()
{
    MyTuple c0(0, 1.5, 2, 3.7);

    // display contents "0 1 2 3"
    cout << get<0>(c0);
    cout << " " << get<1>(c0);
    cout << " " << get<2>(c0);
    cout << " " << get<3>(c0) << endl;

    // display size "4"
    cout << " " << tuple_size<MyTuple>::value << endl;
}
```

```Output
0 1.5 2 3.7
4
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<tuple >

**Header:** \<array > (pro specializaci pole)

**Header:** \<utility > (pro specializaci páru)

**Obor názvů:** std
