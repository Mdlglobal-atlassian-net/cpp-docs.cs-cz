---
title: is_bind_expression – třída
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_bind_expression
helpviewer_keywords:
- is_bind_expression class
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
ms.openlocfilehash: f547b6f74a86612174cb0f510870171158678f7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383656"
---
# <a name="isbindexpression-class"></a>is_bind_expression – třída

Testuje, zda typ generován voláním `bind`.

## <a name="syntax"></a>Syntaxe

Šablona<class Ty> is_bind_expression – struktura {statické konstantní bool hodnotu;};

## <a name="remarks"></a>Poznámky

Konstantní členské `value` má hodnotu true Pokud typ `Ty` je typ vrácený voláním `bind`; jinak hodnota false.

## <a name="example"></a>Příklad

```cpp
// std__functional__is_bind_expression.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

template<class Expr>
void test_for_bind(const Expr&)
{
    std::cout << std::is_bind_expression<Expr>::value << std::endl;
}

int main()
{
    test_for_bind(3.0 * 3.0);
    test_for_bind(std::bind(square, 3));

    return (0);
}
```

```Output
0
1
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Vytvoření vazby](../standard-library/functional-functions.md#bind)<br/>
