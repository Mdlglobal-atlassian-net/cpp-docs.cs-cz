---
title: Chyba kompilátoru C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 4c87e98f11a560d0d92be8ea7bc624edd4e09ad2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201393"
---
# <a name="compiler-error-c3286"></a>Chyba kompilátoru C3286

> *specifikátor*: proměnná iterace nemůže mít žádné specifikátory třídy úložiště.

Třída úložiště nemůže být určena pro proměnnou iterace. Další informace naleznete v tématu [třídy úložiště (C++)](../../cpp/storage-classes-cpp.md) a [pro každý v](../../dotnet/for-each-in.md).

## <a name="example"></a>Příklad

Následující ukázka vygeneruje C3286 a také zobrazí správné použití.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```
