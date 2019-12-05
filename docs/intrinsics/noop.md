---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: aec4df98413bf34ac1e2966d012bb905edd4775e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857928"
---
# <a name="__noop"></a>__noop

**Specifické pro společnost Microsoft**

Vnitřní `__noop` určuje, že by měla být funkce ignorována. Seznam argumentů je analyzován, ale pro argumenty není vygenerován žádný kód. Je určena pro použití v globálních ladicích funkcích, které přijímají proměnný počet argumentů.

Kompilátor převede v době kompilace vnitřní `__noop` na 0.

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
