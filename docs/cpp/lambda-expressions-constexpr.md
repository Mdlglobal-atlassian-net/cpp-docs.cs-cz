---
title: constexpr – výrazy Lambda v jazyce C++ | Dokumentace Microsoftu
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
ms.openlocfilehash: b78fa3de7777ffc6702902cf967a405595caf12f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408200"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr – výrazy Lambda v jazyce C++
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
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)   
 [Objekty funkcí ve standardní knihovně C++](../standard-library/function-objects-in-the-stl.md)   
 [Volání funkce](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)