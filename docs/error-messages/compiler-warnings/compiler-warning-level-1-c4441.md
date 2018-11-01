---
title: Kompilátor upozornění (úroveň 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: 45d7a6af09677c1e63dab5ffcc55c35d8203b40b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539695"
---
# <a name="compiler-warning-level-1-c4441"></a>Kompilátor upozornění (úroveň 1) C4441

konvence volání cc1 ignorovány; Místo toho použita cc2

Členské funkce ve spravované uživatelem definovaných typů a obecných typů globální funkce musí použít [__clrcall](../../cpp/clrcall.md) konvence volání.  Kompilátor používá `__clrcall`.

## <a name="example"></a>Příklad

Následující ukázka generuje C4441.

```
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```