---
title: Upozornění kompilátoru (úroveň 1) C4305
ms.date: 01/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: dc718e5f7ebe9478ed1bf2a7323db940935cb1d6
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926124"
---
# <a name="compiler-warning-level-1-c4305"></a>Upozornění kompilátoru (úroveň 1) C4305

> '*Context*': zkrácení z '*typ1*' na '*typ2*'

## <a name="remarks"></a>Poznámky

Toto upozornění je vystaveno, pokud je hodnota převedena na menší typ v inicializaci nebo jako argument konstruktoru, což vede ke ztrátě informací.

## <a name="example"></a>Příklad

Tato ukázka ukazuje dva způsoby, jak se může zobrazit toto upozornění:

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

Chcete-li tento problém vyřešit, proveďte inicializaci pomocí hodnoty správného typu nebo použijte explicitní přetypování na správný typ. Například použijte literál **typu float** jako 2.71828 f namísto **Double** (výchozí typ pro literály s plovoucí desetinnou čárkou) pro inicializaci proměnné **typu float** nebo předejte konstruktoru, který přijímá argument **typu float** .
