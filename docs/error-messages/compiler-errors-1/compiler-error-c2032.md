---
title: Chyba kompilátoru C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: 5743aba880f23d7706940936fc4a3a1973a84ca1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558246"
---
# <a name="compiler-error-c2032"></a>Chyba kompilátoru C2032

'identifier': funkce nemůže být členem struktury nebo sjednocení "structorunion.

Struktura nebo sjednocení má členská funkce, který je povolen v jazyce C++, ale ne v C. Chcete-li vyřešit chybu, zkompiluje kód jako programu v jazyce C++ nebo odeberte členskou funkci.

Následující ukázka generuje C2032:

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

Možná řešení:

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```