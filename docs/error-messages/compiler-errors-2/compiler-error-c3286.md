---
title: Chyba kompilátoru C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 8c09ea34c7dabf2cadecad7c76d766c9496f5a5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461006"
---
# <a name="compiler-error-c3286"></a>Chyba kompilátoru C3286

> "*specifikátor*': Proměnná iterace nemůže mít žádné specifikátory třídy úložiště

Iterační proměnné nelze zadat třídu úložiště. Další informace najdete v tématu [třídy úložiště (C++)](../../cpp/storage-classes-cpp.md) a [u každé v](../../dotnet/for-each-in.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3286 a také ukazuje správné použití.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```