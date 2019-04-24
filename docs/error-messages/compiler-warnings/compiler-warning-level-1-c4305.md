---
title: Kompilátor upozornění (úroveň 1) C4305
ms.date: 1/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 3f9116b0e7bdd9ee13c42b48f44da4b090f41ccd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327467"
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
