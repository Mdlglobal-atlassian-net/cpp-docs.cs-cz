---
title: výrazy lambda constexpr vC++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 9467d9e404204012df6461adacd5dc4cdbdfe71d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179572"
---
# <a name="constexpr-lambda-expressions-in-c"></a>výrazy lambda constexpr vC++

**Visual Studio 2017 verze 15,3 a novější** (k dispozici s [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): výraz lambda může být deklarován jako **constexpr** nebo použit v konstantním výrazu, pokud je v rámci konstantního výrazu povolena inicializace každého datového člena, který zachycuje nebo zavádí.

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

Lambda je implicitně **constexpr** , pokud výsledek splňuje požadavky funkce **constexpr** :

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Pokud je lambda implicitně nebo explicitně **constexpr**a převedete ho na ukazatel na funkci, výsledná funkce je také **constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Objekty funkcí ve standardní knihovně C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Volání funkcí](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
