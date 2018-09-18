---
title: Upozornění (úroveň 1) C4835 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4835
dev_langs:
- C++
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70492be13d312c5d167990cfa0b6c0d741e1055f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080100"
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