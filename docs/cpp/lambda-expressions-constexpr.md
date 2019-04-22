---
title: constexpr výrazy lambda v jazyce C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: d1bc60a6da813e54c857da38b0164f544216be00
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59424180"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr výrazy lambda v jazyce C++

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): Výraz lambda může být deklarována jako **constexpr** nebo při inicializaci každého datového člena, který zachycuje nebo zavádí je povolený v konstantním výrazu v konstantním výrazu.

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