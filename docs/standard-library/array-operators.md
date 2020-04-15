---
title: '&lt;operátory polí&gt;'
ms.date: 11/04/2016
f1_keywords:
- array/std::array::operator!=
- array/std::array::operator<
- array/std::array::operator<=
- array/std::array::operator>
- array/std::array::operator>=
- array/std::array::operator==
ms.assetid: c8f46282-f179-4909-9a01-639cb8e18c27
ms.openlocfilehash: 531ad2936322f90a38631a9450e0ad8a210fdd87
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364902"
---
# <a name="ltarraygt-operators"></a>&lt;operátory polí&gt;

Záhlaví \<pole> obsahuje **tyto** funkce šablony porovnání bez člena.

||||
|-|-|-|
|[operátor!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|
|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|[operátor==](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>operátor!=

Porovnání pole, není stejné.

```cpp
template <Ty, std::size_t N>
bool operator!=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ prvku

*N*\
Velikost pole.

*Vlevo*\
Levý kontejner k porovnání.

*Právo*\
Správný kontejner k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony `!(left == right)`vrátí .

### <a name="example"></a>Příklad

```cpp
// std__array__operator_ne.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 != c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 != c1);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
false
true
```

## <a name="operatorlt"></a><a name="op_lt"></a>Operátor&lt;

Porovnání pole, menší než.

```cpp
template <Ty, std::size_t N>
bool operator<(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ prvku

*N*\
Velikost pole.

*Vlevo*\
Levý kontejner k porovnání.

*Právo*\
Správný kontejner k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony přetíží `operator<` porovnání dvou objektů [třídy](../standard-library/array-class-stl.md)třídy šablony pole Class . Funkce vrátí `lexicographical_compare(left.begin(), left.end(), right.begin())`.

### <a name="example"></a>Příklad

```cpp
// std__array__operator_lt.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 < c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 < c1);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
false
true
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operátor&lt;=

Porovnání pole, menší než nebo rovno.

```cpp
template <Ty, std::size_t N>
bool operator<=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ prvku

*N*\
Velikost pole.

*Vlevo*\
Levý kontejner k porovnání.

*Právo*\
Správný kontejner k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony `!(right < left)`vrátí .

### <a name="example"></a>Příklad

```cpp
// std__array__operator_le.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 <= c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c1 <= c0);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
true
false
```

## <a name="operator"></a><a name="op_eq_eq"></a>operátor==

Porovnání pole, stejné.

```cpp
template <Ty, std::size_t N>
bool operator==(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ prvku

*N*\
Velikost pole.

*Vlevo*\
Levý kontejner k porovnání.

*Právo*\
Správný kontejner k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony přetíží `operator==` porovnání dvou objektů [třídy](../standard-library/array-class-stl.md)třídy šablony pole Class . Funkce vrátí `equal(left.begin(), left.end(), right.begin())`.

### <a name="example"></a>Příklad

```cpp
// std__array__operator_eq.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 == c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 == c1);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
true
false
```

## <a name="operatorgt"></a><a name="op_gt"></a>Operátor&gt;

Porovnání polí, větší než.

```cpp
template <Ty, std::size_t N>
bool operator>(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ prvku

*N*\
Velikost pole.

*Vlevo*\
Levý kontejner k porovnání.

*Právo*\
Správný kontejner k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony `(right < left)`vrátí .

### <a name="example"></a>Příklad

```cpp
// std__array__operator_gt.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 > c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c1 > c0);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
false
true
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operátor&gt;=

Porovnání pole, větší než nebo rovno.

```cpp
template <Ty, std::size_t N>
bool operator>=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ prvku

*N*\
Velikost pole.

*Vlevo*\
Levý kontejner k porovnání.

*Právo*\
Správný kontejner k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony `!(left < right)`vrátí .

### <a name="example"></a>Příklad

```cpp
// std__array__operator_ge.cpp
// compile with: /EHsc
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
    {
    Myarray c0 = {0, 1, 2, 3};

// display contents " 0 1 2 3"
    for (Myarray::const_iterator it = c0.begin();
        it != c0.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

    Myarray c1 = {4, 5, 6, 7};

// display contents " 4 5 6 7"
    for (Myarray::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " " << *it;
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 >= c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 >= c1);
    std::cout << std::endl;

    return (0);
    }
```

```Output
0 1 2 3
4 5 6 7
true
false
```

## <a name="see-also"></a>Viz také

[\<>pole](../standard-library/array.md)
