---
title: is_union – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_union
dev_langs:
- C++
helpviewer_keywords:
- is_union class
- is_union
ms.assetid: 80eda256-40b8-4db5-9ac1-d58bb8032a3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 433e3ab596fb5f7b2399e2834e78e84366e4c56c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109937"
---
# <a name="isunion-class"></a>is_union – třída

Testuje, zda je typ sjednocení.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_union;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je typ sjednocení nebo `cv-qualified` formulář typu sjednocení, jinak má hodnotu false.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_union.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

union ints
    {
    int in;
    long lo;
    };

int main()
    {
    std::cout << "is_union<trivial> == " << std::boolalpha
        << std::is_union<trivial>::value << std::endl;
    std::cout << "is_union<int> == " << std::boolalpha
        << std::is_union<int>::value << std::endl;
    std::cout << "is_union<ints> == " << std::boolalpha
        << std::is_union<ints>::value << std::endl;

    return (0);
    }

```

```Output
is_union<trivial> == false
is_union<int> == false
is_union<ints> == true
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_class – třída](../standard-library/is-class-class.md)<br/>
