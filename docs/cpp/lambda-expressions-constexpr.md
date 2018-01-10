---
title: "Výrazy Lambda v jazyce C++ constexpr | Microsoft Docs"
ms.custom: 
ms.date: 07/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
caps.latest.revision: "0"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 307ce6ab87ca36de561ebcf1ad8bd30eb73e4192
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr výrazy Lambda v jazyce C++
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): výrazu lambda může být deklarována jako `constexpr` nebo ve výrazu dosažení konstantních při inicializaci každý člen data to zaznamená nebo zavádí je povoleno v rámci konstantní výraz.  

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
Lambda je implicitně `constexpr` Pokud svůj výsledek splňuje požadavky `constexpr` funkce:
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Pokud lambda implicitně nebo explicitně `constexpr`a můžete ho převést na ukazatel na funkci, výsledná funkce je také `constexpr`:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Objekty funkcí ve standardní knihovně C++](../standard-library/function-objects-in-the-stl.md)   
 [Volání funkce](../cpp/function-call-cpp.md)   
 [for_each –](../standard-library/algorithm-functions.md#for_each)