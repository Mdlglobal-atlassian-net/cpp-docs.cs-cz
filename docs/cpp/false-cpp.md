---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: 5fc27c7f1dfde7d1f686f0a752652773ade9cc0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464061"
---
# <a name="false-c"></a>false (C++)

Klíčové slovo je jednou ze dvou hodnot proměnné typu [bool](../cpp/bool-cpp.md) nebo podmíněného výrazu (podmíněný výraz je nyní **true** logický výraz). Například pokud `i` je proměnná typu **bool**, `i = false;` příkaz přiřadí **false** k `i`.

## <a name="example"></a>Příklad

```cpp
// bool_false.cpp
#include <stdio.h>

int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)