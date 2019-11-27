---
title: Upozornění kompilátoru (úroveň 4) C4100
ms.date: 11/04/2016
f1_keywords:
- C4100
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
ms.openlocfilehash: 80794d270b40a8f40d44630da70455c015158423
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541234"
---
# <a name="compiler-warning-level-4-c4100"></a>Upozornění kompilátoru (úroveň 4) C4100

' identifier ': formální parametr bez odkazu

Na formální parametr se neodkazuje v těle funkce. Parametr, který není odkazem, se ignoruje.

C4100 může být také vystavena, pokud kód volá destruktor v jiném neodkazovaném parametru primitivního typu.  Toto je omezení kompilátoru Microsoftu C++ .

Následující ukázka generuje C4100:

```cpp
// C4100.cpp
// compile with: /W4
void func(int i) {   // C4100, delete the unreferenced parameter to
                     //resolve the warning
   // i;   // or, add a reference like this
}

int main()
{
   func(1);
}
```