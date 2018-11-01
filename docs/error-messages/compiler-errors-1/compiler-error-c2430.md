---
title: Chyba kompilátoru C2430
ms.date: 11/04/2016
f1_keywords:
- C2430
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
ms.openlocfilehash: 754758e652539e4f2d9b12e568b8ef5ccf41d8db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676470"
---
# <a name="compiler-error-c2430"></a>Chyba kompilátoru C2430

registrovat více než jeden index v 'identifier'

Více než jeden registr je škálovat. Kompilátor podporuje škálován indexování, ale je možné škálovat pouze jeden registr.

## <a name="example"></a>Příklad

Následující ukázka generuje C2430.

```
// C2430.cpp
// processor: x86
int main() {
   _asm mov eax, [ebx*2+ecx*4] // C2430
}
```