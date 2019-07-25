---
title: Třída integral_constant, třída bool_constant
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
ms.openlocfilehash: c85da1f3be7821f8d82cd2b19dab2a5864426a5a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452049"
---
# <a name="integralconstant-class-boolconstant-class"></a>Třída integral_constant, třída bool_constant

Provede celočíselnou konstantu z typu a hodnoty.

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

*Š*\
Typ konstanty.

*ICES*\
Hodnota konstanty.

## <a name="remarks"></a>Poznámky

Třída šablony, při specializované s celočíselným typem *T* a hodnotou v typu, představuje objekt, který obsahuje konstantu tohoto integrálního typu se zadanou hodnotou.  `integral_constant` Člen s názvem `type` je alias pro generovaný typ specializace šablony `value` a člen obsahuje hodnotu *v* použitou k vytvoření specializace.

Třída šablony je `integral_constant` explicitní Částečná specializace, která jako argument *T* používá **bool.** `bool_constant`

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

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[< type_traits >](../standard-library/type-traits.md)\
[false_type](../standard-library/type-traits-typedefs.md#false_type)\
[true_type](../standard-library/type-traits-typedefs.md#true_type)
