---
title: Chyba kompilátoru C2561 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8611af23ab884a853fc751ae82c636753993495b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070701"
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