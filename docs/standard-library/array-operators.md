---
title: "&lt;pole&gt; operátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- array/std::array::operator!=
- array/std::array::operator<
- array/std::array::operator<=
- array/std::array::operator>
- array/std::array::operator>=
- array/std::array::operator==
dev_langs: C++
ms.assetid: c8f46282-f179-4909-9a01-639cb8e18c27
caps.latest.revision: "12"
manager: ghogen
ms.openlocfilehash: e4854303bc80603ccbdf908aefc31f304487fb1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltarraygt-operators"></a>&lt;pole&gt; operátory
\<Pole > Hlavička zahrnuje tyto `array` třetí porovnání šablony funkcí.  
  
||||  
|-|-|-|  
|[Operator! =](#op_neq)|[operátor&gt;](#op_gt)|[operátor&gt;=](#op_gt_eq)|  
|[operátor&lt;](#op_lt)|[operátor&lt;=](#op_lt_eq)|[Operator ==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>Operator! =  
 Pole porovnání, není rovno.  
  
```  
template <Ty, std::size_t N>  
bool operator!=(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ prvku  
  
 `N`  
 Velikost pole.  
  
 `left`  
 Levé kontejner k porovnání.  
  
 `right`  
 Správném kontejneru k porovnání.  
  
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
  
##  <a name="op_lt"></a>operátor&lt;  
 Pole porovnání, menší než.  
  
```  
template <Ty, std::size_t N>  
bool operator<(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ prvku  
  
 `N`  
 Velikost pole.  
  
 `left`  
 Levé kontejner k porovnání.  
  
 `right`  
 Správném kontejneru k porovnání.  
  
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
  
##  <a name="op_lt_eq"></a>operátor&lt;=  
 Pole porovnání je menší než nebo rovno.  
  
```  
template <Ty, std::size_t N>  
bool operator<=(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ prvku  
  
 `N`  
 Velikost pole.  
  
 `left`  
 Levé kontejner k porovnání.  
  
 `right`  
 Správném kontejneru k porovnání.  
  
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
  
##  <a name="op_eq_eq"></a>Operator ==  
 Pole porovnání, stejné.  
  
```  
template <Ty, std::size_t N>  
bool operator==(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ prvku  
  
 `N`  
 Velikost pole.  
  
 `left`  
 Levé kontejner k porovnání.  
  
 `right`  
 Správném kontejneru k porovnání.  
  
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
  
##  <a name="op_gt"></a>operátor&gt;  
 Pole porovnání, větší než.  
  
```  
template <Ty, std::size_t N>  
bool operator>(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ prvku  
  
 `N`  
 Velikost pole.  
  
 `left`  
 Levé kontejner k porovnání.  
  
 `right`  
 Správném kontejneru k porovnání.  
  
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
  
##  <a name="op_gt_eq"></a>operátor&gt;=  
 Porovnání pole, větší než nebo rovno.  
  
```  
template <Ty, std::size_t N>  
bool operator>=(
    const array<Ty, N>& left,  
    const array<Ty, N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ prvku  
  
 `N`  
 Velikost pole.  
  
 `left`  
 Levé kontejner k porovnání.  
  
 `right`  
 Správném kontejneru k porovnání.  
  
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
 [\<pole >](../standard-library/array.md)

