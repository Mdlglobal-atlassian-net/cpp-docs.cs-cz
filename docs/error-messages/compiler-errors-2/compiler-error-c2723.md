---
title: Chyba kompilátoru C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: bc07a99f12ed0e447427990969e54f7f3d3d3b7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635384"
---
# <a name="compiler-error-c2723"></a>Chyba kompilátoru C2723

'function': "specifikátor" specifikátor není platný v definici funkce

Specifikátor nemůže být použit s definicí funkce mimo deklaraci třídy. `virtual` Specifikátor se dá nastavit jenom v deklaraci členské funkce v deklaraci třídy.

Následující ukázka generuje C2723 a ukazuje, jak ho opravit:

```
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```