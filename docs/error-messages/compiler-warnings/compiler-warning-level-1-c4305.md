---
title: "Kompilátoru (úroveň 1) upozornění C4305 | Microsoft Docs"
ms.custom: 
ms.date: 1/17/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe4b2b420c44584fdd5b4d48b4264bbc7a51bee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="compiler-warning-level-1-c4305"></a>C4305 kompilátoru upozornění (úroveň 1)

> '*kontextu*': zkrácení z '*type1*'do'*type2*.  

## <a name="remarks"></a>Poznámky

Se objeví toto upozornění, když je hodnota převedena na menší typ v inicializaci nebo jako argument konstruktoru, což vede ke ztrátě informací.

## <a name="example"></a>Příklad

Tato ukázka obsahuje dva způsoby, jak vám může tento stav zapříčinit:

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

Chcete-li tento problém vyřešit, inicializovat pomocí hodnoty správného typu nebo použijte explicitní přetypování do správného typu. Například použít **float** literálu například 2.71828f místo **dvojité** (výchozí typ pro literály s plovoucí desetinnou čárkou) k chybě při inicializaci **float** proměnnou, nebo mají být předány konstruktor, který přebírá **float** argument.
