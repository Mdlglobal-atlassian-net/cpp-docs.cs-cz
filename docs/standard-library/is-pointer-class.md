---
title: is_pointer – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_pointer class
- is_pointer
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf9f05b77adc7d989d37afcbce040405ccbfdf03
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852107"
---
# <a name="ispointer-class"></a>is_pointer – třída

Testy, pokud je ukazatel typu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_pointer;
```

### <a name="parameters"></a>Parametry

`Ty` Typ k dotazu.

## <a name="remarks"></a>Poznámky

Instance predikátem typu obsahuje hodnotu true, pokud typ `Ty` je ukazatel na `void`, a ukazatel na objekt, nebo a ukazatel na funkci nebo `cv-qualified` formu jeden z nich, jinak má hodnotu false. Všimněte si, že `is_pointer` blokování false v případě `Ty` je ukazatel na člena nebo odkazy – členská funkce.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_pointer<trivial> == " << std::boolalpha
        << std::is_pointer<trivial>::value << std::endl;
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha
        << std::is_pointer<int trivial::*>::value << std::endl;
    std::cout << "is_pointer<trivial *> == " << std::boolalpha
        << std::is_pointer<trivial *>::value << std::endl;
    std::cout << "is_pointer<int> == " << std::boolalpha
        << std::is_pointer<int>::value << std::endl;
    std::cout << "is_pointer<int *> == " << std::boolalpha
        << std::is_pointer<int *>::value << std::endl;

    return (0);
    }

```

```Output
is_pointer<trivial> == false
is_pointer<int trivial::*> == false
is_pointer<trivial *> == true
is_pointer<int> == false
is_pointer<int *> == true
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer – třída](../standard-library/is-member-pointer-class.md)<br/>
[is_reference – třída](../standard-library/is-reference-class.md)<br/>
