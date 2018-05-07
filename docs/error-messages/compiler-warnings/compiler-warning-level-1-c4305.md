---
title: Kompilátoru (úroveň 1) upozornění C4305 | Microsoft Docs
ms.custom: ''
ms.date: 1/17/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7694c511f57b6907227d62f969b61218f836cb14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
