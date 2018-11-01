---
title: Chyba kompilátoru C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 13840246a5dc6a1c1bdbcb55dc47f212ee353d81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561197"
---
# <a name="compiler-error-c2513"></a>Chyba kompilátoru C2513

'type': deklarovaná žádná proměnná před '='

Specifikátor typu se zobrazí v deklaraci s identifikátorem žádné proměnné.

Následující ukázka generuje C2513:

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Tato chyba může být také generovány jako důsledek kompilátoru shoda práce pro Visual Studio .NET 2003: Inicializace již není povolena definice typu. Inicializace definice typu není povolený Standard a nyní generuje chybu kompilátoru.

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Alternativou může být odstranění `typedef` k definování proměnné s agregační inicializátor seznamu, ale to se nedoporučuje, protože ho vytvořit proměnnou se stejným názvem jako typ, který se skrýt název typu.