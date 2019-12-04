---
title: Chyba kompilátoru C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: b4a14be9cd32c752e2ab889417494e80b935e31b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755561"
---
# <a name="compiler-error-c2561"></a>Chyba kompilátoru C2561

' identifier ': funkce musí vracet hodnotu

Funkce byla deklarována jako vrácení hodnoty, ale definice funkce neobsahuje příkaz `return`.

Tato chyba může být způsobena nesprávný prototyp funkce:

1. Pokud funkce nevrátí hodnotu, Deklarujte funkci s návratovým typem [void](../../cpp/void-cpp.md).

1. Ověřte, zda všechny možné větve funkce vracejí hodnotu typu deklarovaného v prototypu.

1. C++funkce obsahující rutiny vloženého sestavení, které ukládají vrácenou hodnotu v registru `AX`, mohou potřebovat návratový příkaz. Zkopírujte hodnotu v `AX` na dočasnou proměnnou a vraťte tuto proměnnou z funkce.

Následující ukázka generuje C2561:

```cpp
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```
