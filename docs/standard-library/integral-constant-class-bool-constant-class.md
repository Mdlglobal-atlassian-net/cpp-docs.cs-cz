---
title: integral_constant – třída, bool_constant – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs:
- C++
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 053816fcf18ec29b5e405f84b545432e848d2b59
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104007"
---
# <a name="integralconstant-class-boolconstant-class"></a>integral_constant – třída, bool_constant – třída

Díky integrální konstantní typ a hodnotu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, T v>
struct integral_constant {
   static constexpr T value = v;
   typedef T value_type;
   typedef integral_constant<T, v> type;
   constexpr operator value_type() const noexcept;
   constexpr value_type operator()() const noexcept;
   };
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ konstanty.

*v*<br/>
Hodnota konstanty.

## <a name="remarks"></a>Poznámky

`integral_constant` Třída šablony, když specializovaný s celočíselného typu *T* a hodnotu *v* tohoto typu, představuje objekt, který obsahuje konstantu daného celočíselného typu se zadanou hodnotou. Člen s názvem `type` je alias pro typ specializace vygenerovanou šablonu a `value` člena obsahuje hodnotu *v* použitý k vytvoření specializaci.

`bool_constant` Je explicitní částečné specializace šablony třídy `integral_constant` , která používá **bool** jako *T* argument.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__integral_constant.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "integral_constant<int, 5> == "
        << std::integral_constant<int, 5>::value << std::endl;
    std::cout << "integral_constant<bool, false> == " << std::boolalpha
        << std::integral_constant<bool, false>::value << std::endl;

    return (0);
    }

```

```Output
integral_constant<int, 5> == 5
integral_constant<bool, false> == false
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
[false_type](../standard-library/type-traits-typedefs.md#false_type)<br/>
[true_type](../standard-library/type-traits-typedefs.md#true_type)<br/>
