---
title: __noop | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __noop_cpp
- __noop
dev_langs:
- C++
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97820367f0960925dfcac1db339260cd3f52b8bc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430212"
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