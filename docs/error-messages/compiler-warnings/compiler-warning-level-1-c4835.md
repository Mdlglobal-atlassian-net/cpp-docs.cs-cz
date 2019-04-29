---
title: Kompilátor upozornění (úroveň 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: 0427a97a9e368a19a40a8d1a552f7713e36f831e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380848"
---
# <a name="compiler-warning-level-1-c4835"></a>Kompilátor upozornění (úroveň 1) C4835

'variable': inicializátor pro exportovaná data se nespustí, dokud se v hostitelském sestavení nejdřív nespustí spravovaný kód

Při přístupu k datům mezi spravované součásti, se doporučuje není použít nativní C++ import a export mechanismy. Místo toho deklarovat datových členů uvnitř spravovaného typu a odkazovat na metadata se `#using` v klientovi. Další informace najdete v tématu [# direktiva using](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4835.

```
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Příklad

Následující příklad využívá komponenty sestavené v předchozí ukázce zobrazující, že je hodnota proměnné není podle očekávání.

```
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```