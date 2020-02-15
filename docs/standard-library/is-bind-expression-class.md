---
title: is_bind_expression – třída
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_bind_expression
helpviewer_keywords:
- is_bind_expression class
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
ms.openlocfilehash: 9d83ff978ccbaec5e66509ac94f22cf29bc20866
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258079"
---
# <a name="is_bind_expression-class"></a>is_bind_expression – třída

Testuje, zda typ generovaný voláním `bind`.

## <a name="syntax"></a>Syntaxe

```cpp
template<class Ty>
struct is_bind_expression {
   static const bool value;
};
```

## <a name="remarks"></a>Poznámky

Konstanta členu `value` je true, pokud typ `Ty` je typ vrácený voláním `bind`, jinak false.

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
