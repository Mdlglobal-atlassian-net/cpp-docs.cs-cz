---
title: Less – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::less
dev_langs:
- C++
helpviewer_keywords:
- less struct
- less function
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fac4528c976e99a77ceec8bc170323846a0e3a28
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="less-struct"></a>less – struktura

Predikát binární, který provádí je menší – než operaci ( `operator<`) na její argumenty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type = void>
struct less : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<
template <>
struct less<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) <std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

`Type`, `T`, `U` Žádný typ, který podporuje `operator<` , která má operandy zadán nebo odvozené typy.

`Left` Levý operand je menší – než operaci. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `T`.

`Right` Pravý operand je menší – než operaci. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `U`.

## <a name="return-value"></a>Návratová hodnota

Výsledek `Left < Right`. Specializované šablony ideální předávání výsledku, který má typ, který je vrácen rutinou `operator<`.

## <a name="remarks"></a>Poznámky

Binární predikát `less` <  `Type`> poskytuje striktní slabé řazení sady hodnot element typu `Type` do třídy ekvivalenční jenom v případě tohoto typu splňuje požadavky na standardní matematické pro proto řazen. Specializací pro jakýkoli typ ukazatele yield celkový řazení elementů v tom, že všechny elementy odlišné hodnoty jsou seřazené s ohledem na sebe navzájem.

## <a name="example"></a>Příklad

```cpp
// functional_less.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

struct MyStruct {
   MyStruct(int i) : m_i(i){}

   bool operator < (const MyStruct & rhs) const {
      return m_i < rhs.m_i;
   }

   int m_i;
};

int main() {
   using namespace std;
   vector <MyStruct> v1;
   vector <MyStruct>::iterator Iter1;
   vector <MyStruct>::reverse_iterator rIter1;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
       v1.push_back( MyStruct(rand()));

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   sort( v1.begin( ), v1.end( ), less<MyStruct>());

   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )
cout << Iter1->m_i << " ";
   cout << ")" << endl;
 }
```

## <a name="output"></a>Výstup

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500)
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
