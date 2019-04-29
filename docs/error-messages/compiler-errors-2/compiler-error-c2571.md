---
title: Chyba kompilátoru C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: d7d4898e5f0b55c50a4c18cef053cc150394d7e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408574"
---
# <a name="compiler-error-c2571"></a>Chyba kompilátoru C2571

'function': virtuální funkce nemůže být sjednocení "sjednocení.

Sjednocení je deklarován s virtuální funkcí. Je možné deklarovat pouze ve třídě nebo struktuře virtuální funkce.  Možná řešení:

1. Změňte sjednocení na třídu nebo strukturu.

1. Ujistěte se, funkce nevirtuální.

Následující ukázka generuje C2571:

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```