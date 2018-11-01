---
title: Kompilátor upozornění (úroveň 1) C4817
ms.date: 11/04/2016
f1_keywords:
- C4817
helpviewer_keywords:
- C4817
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
ms.openlocfilehash: bb6eb8899efdab3cae39f77079f7eed72344acc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666871"
---
# <a name="compiler-warning-level-1-c4817"></a>Kompilátor upozornění (úroveň 1) C4817

'member': Neplatné použití "." pro přístup k tomuto členu; nahrazení kompilátoru znaky ->"

Byl použit nesprávný členský operátor přístupu.

## <a name="example"></a>Příklad

Následující ukázka generuje C4817.

```
// C4817.cpp
// compile with: /clr /W1
using namespace System;
int main() {
   array<Int32> ^ a = gcnew array<Int32>(100);
   Console::WriteLine( a.Length );   // C4817
   Console::WriteLine( a->Length );   // OK
}
```
