---
title: is_floating_point – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_floating_point
dev_langs:
- C++
helpviewer_keywords:
- is_floating_point class
- is_floating_point
ms.assetid: 070679c1-115b-4ee4-8ab7-f52e5d9e157f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6410cf6a6f3496daad7aebeb352b3a37497b821
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110250"
---
# <a name="isfloatingpoint-class"></a>is_floating_point – třída

Testuje, zda je typ je s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_floating_point;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je plovoucí typ bodu nebo `cv-qualified` formu plovoucí desetinnou čárkou typu, v opačném případě obsahuje hodnotu false.

A s plovoucí desetinnou čárkou typu bodu je jedním z **float**, **double**, nebo **long double**.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_floating_point.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_floating_point<trivial> == " << std::boolalpha
        << std::is_floating_point<trivial>::value << std::endl;
    std::cout << "is_floating_point<int> == " << std::boolalpha
        << std::is_floating_point<int>::value << std::endl;
    std::cout << "is_floating_point<float> == " << std::boolalpha
        << std::is_floating_point<float>::value << std::endl;

    return (0);
    }

```

```Output
is_floating_point<trivial> == false
is_floating_point<int> == false
is_floating_point<float> == true
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_integral – třída](../standard-library/is-integral-class.md)<br/>
