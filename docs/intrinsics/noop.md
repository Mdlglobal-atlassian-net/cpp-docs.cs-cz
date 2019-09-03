---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 24ba85b1fbbba4491c03d5a81afae345228db3bd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217180"
---
# <a name="__noop"></a>__noop

**Specifické pro společnost Microsoft**

`__noop` Vnitřní určuje, že by funkce měla být ignorována. Seznam argumentů je analyzován, ale pro argumenty není vygenerován žádný kód. Je určena pro použití v globálních ladicích funkcích, které přijímají proměnný počet argumentů.

Kompilátor převede `__noop` vnitřní hodnotu na 0 v době kompilace.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak můžete použít `__noop`.

```cpp
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

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
