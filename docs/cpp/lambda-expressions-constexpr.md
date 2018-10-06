---
title: constexpr výrazy lambda v jazyce C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71c28ab1531c2af19f2b8f594db457d0272b0664
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820357"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr výrazy lambda v jazyce C++

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): výraz lambda může být deklarována jako **constexpr** nebo použít ve výrazu dosažení konstantních při inicializaci jednotlivých datový člen, který zachycuje nebo zavádí je povolený v konstantním výrazu.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

Výraz lambda je implicitně **constexpr** Pokud výsledek splňuje požadavky **constexpr** funkce:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Pokud je výraz lambda implicitně nebo explicitně **constexpr**a převést na ukazatel na funkci, je výsledný funkce také **constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Objekty funkcí ve standardní knihovně C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Volání funkcí](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)