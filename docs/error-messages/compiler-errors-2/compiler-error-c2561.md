---
title: Chyba kompilátoru C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: 8350c5baf129b88c178be280d2da7fe856c6cf57
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517608"
---
# <a name="compiler-error-c2561"></a>Chyba kompilátoru C2561

'identifier': funkce musí vracet hodnotu

Funkce byla deklarována jako návratová hodnota, ale neobsahuje definici funkce `return` příkazu.

Tuto chybu může způsobovat nesprávné funkci prototyp:

1. Pokud funkce nevrací hodnotu, deklarujte funkci s návratovým typem [void](../../cpp/void-cpp.md).

1. Zkontrolujte, že všechny možné větve funkce vrátí hodnotu typu deklarované v prototypu.

1. Funkce jazyka C++ obsahující vložené sestavení rutin, které uložení návratové hodnoty v `AX` registrace může být nutné příkaz return. Zkopírujte hodnotu v `AX` k dočasné proměnné a tuto proměnnou vrácení z funkce.

Následující ukázka generuje C2561:

```
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