---
title: is_placeholder – třída
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 2c7848c88194a9b541867b26ffe27764ad862503
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413629"
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

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[_1 – objekt](../standard-library/1-object.md)<br/>
