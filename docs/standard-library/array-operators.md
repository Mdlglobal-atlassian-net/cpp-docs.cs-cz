---
title: '&lt;pole&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- array/std::array::operator!=
- array/std::array::operator<
- array/std::array::operator<=
- array/std::array::operator>
- array/std::array::operator>=
- array/std::array::operator==
dev_langs:
- C++
ms.assetid: c8f46282-f179-4909-9a01-639cb8e18c27
caps.latest.revision: 12
manager: ghogen
ms.openlocfilehash: 7ddd350bc3959e67d88d77a0d64d42a26d48e786
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltarraygt-operators"></a>&lt;pole&gt; operátory

\<Pole > Hlavička zahrnuje tyto `array` třetí porovnání šablony funkcí.

||||
|-|-|-|
|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|
|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  Operator! =

Pole porovnání, není rovno.

```cpp
template <Ty, std::size_t N>
bool operator!=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

`Ty` Typ elementu.

`N` Velikost pole.

`left` Levé kontejner k porovnání.

`right` Správném kontejneru k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí `!(left == right)`.

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

## <a name="op_lt"></a>  Operátor&lt;

Pole porovnání, menší než.

```cpp
template <Ty, std::size_t N>
bool operator<(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

`Ty` Typ elementu.

`N` Velikost pole.

`left` Levé kontejner k porovnání.

`right` Správném kontejneru k porovnání.

### <a name="remarks"></a>Poznámky

Přetížení funkce šablony `operator<` k porovnání dvou objektů třídy šablony [array – třída](../standard-library/array-class-stl.md). Funkce vrátí hodnotu `lexicographical_compare(left.begin(), left.end(), right.begin())`.

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

## <a name="op_lt_eq"></a>  Operátor&lt;=

Pole porovnání je menší než nebo rovno.

```cpp
template <Ty, std::size_t N>
bool operator<=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

`Ty` Typ elementu.

`N` Velikost pole.

`left` Levé kontejner k porovnání.

`right` Správném kontejneru k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí `!(right < left)`.

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

## <a name="op_eq_eq"></a>  Operator ==

Pole porovnání, stejné.

```cpp
template <Ty, std::size_t N>
bool operator==(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

`Ty` Typ elementu.

`N` Velikost pole.

`left` Levé kontejner k porovnání.

`right` Správném kontejneru k porovnání.

### <a name="remarks"></a>Poznámky

Přetížení funkce šablony `operator==` k porovnání dvou objektů třídy šablony [array – třída](../standard-library/array-class-stl.md). Funkce vrátí hodnotu `equal(left.begin(), left.end(), right.begin())`.

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

## <a name="op_gt"></a>  Operátor&gt;

Pole porovnání, větší než.

```cpp
template <Ty, std::size_t N>
bool operator>(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

`Ty` Typ elementu.

`N` Velikost pole.

`left` Levé kontejner k porovnání.

`right` Správném kontejneru k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí `(right < left)`.

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

## <a name="op_gt_eq"></a>  Operátor&gt;=

Porovnání pole, větší než nebo rovno.

```cpp
template <Ty, std::size_t N>
bool operator>=(
    const array<Ty, N>& left,
    const array<Ty, N>& right);
```

### <a name="parameters"></a>Parametry

`Ty` Typ elementu.

`N` Velikost pole.

`left` Levé kontejner k porovnání.

`right` Správném kontejneru k porovnání.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí `!(left < right)`.

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

[\<pole >](../standard-library/array.md)<br/>
