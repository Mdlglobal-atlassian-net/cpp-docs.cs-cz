---
title: is_placeholder – třída
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 9fa7d4aaade6244fe26f89f3a667598d39471a47
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245162"
---
# <a name="isplaceholder-class"></a>is_placeholder – třída

Testuje, zda je typ je zástupný symbol.

## <a name="syntax"></a>Syntaxe

is_placeholder – struktura {statické const int hodnoty;};

## <a name="remarks"></a>Poznámky

Konstantní hodnota `value` je 0, pokud typ `Ty` není zástupný symbol; v opačném případě je jeho hodnota pozice argument volání funkce, který se váže k. Použijte k určení hodnoty `N` pro n-tý zástupný symbol `_N`.

## <a name="example"></a>Příklad

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```
