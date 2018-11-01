---
title: Chyba kompilátoru C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: 11cb2b83d958f0c59d05034a716a022f00b326ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658676"
---
# <a name="compiler-error-c2553"></a>Chyba kompilátoru C2553

'base_function': přepisující virtuální funkce vrátí typ se liší od "override_function.

Funkce v odvozené třídě se pokusil přepsat virtuální funkce v základní třídě, ale funkce odvozené třídy neměl vracet hodnotu stejného typu jako funkci základní třídy.  Podpis funkce přepsání musí odpovídat signatuře funkce přepsání.

Následující ukázka generuje C2553:

```
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```