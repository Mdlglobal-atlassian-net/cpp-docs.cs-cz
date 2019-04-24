---
title: __noop
ms.date: 11/04/2016
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 674b5170dd2bba7038dfe11af906e31540acd993
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262980"
---
# <a name="noop"></a>__noop

**Microsoft Specific**

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

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)