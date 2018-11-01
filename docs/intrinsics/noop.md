---
title: __noop
ms.date: 11/04/2016
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 074ab4c6ea51c8b3a2543d9b43248a8da37567cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613005"
---
# <a name="noop"></a>__noop

**Specifické pro Microsoft**

`__noop` Vnitřní Určuje, zda mají být ignorovány funkce a analyzovat seznamu argumentů, ale pro argumenty se nevygeneruje žádný kód. Je určena pro použití v globální ladění funkcí, které přijímají proměnný počet argumentů.

Kompilátor převede `__noop` vnitřní na 0 v době kompilace.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak můžete použít `__noop`.

```
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)