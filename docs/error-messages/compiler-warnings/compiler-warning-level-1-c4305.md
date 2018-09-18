---
title: Upozornění (úroveň 1) C4305 kompilátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: 88ae0fb38b7e6af14525906e90486a68ce22ee56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086821"
---
# <a name="compiler-warning-level-1-c4305"></a>Kompilátor upozornění (úroveň 1) C4305

> "*kontextu*': zkrácení z '*type1*"do"*type2*"

## <a name="remarks"></a>Poznámky

Pokud hodnota je převedena na menší typ inicializace nebo jako argument konstruktoru, čímž dojde ke ztrátě informací se objeví toto upozornění.

## <a name="example"></a>Příklad

Tato ukázka zobrazí dva způsoby, jak vám může tento stav zapříčinit:

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

Chcete-li vyřešit tento problém, inicializovat pomocí hodnoty správného typu, nebo použijte explicitní přetypování na správný typ. Například použít **float** literálu jako je například 2.71828f místo **double** (výchozí typ pro literály s plovoucí desetinnou čárkou) k inicializaci **float** proměnné, nebo předat konstruktor, který přijímá **float** argument.
