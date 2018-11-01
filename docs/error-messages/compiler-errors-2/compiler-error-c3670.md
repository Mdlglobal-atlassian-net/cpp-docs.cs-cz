---
title: Chyba kompilátoru C3670
ms.date: 11/04/2016
f1_keywords:
- C3670
helpviewer_keywords:
- C3670
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
ms.openlocfilehash: d3acfd9d4d09c53fac0b2c5a2462c56dfd54e6d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598546"
---
# <a name="compiler-error-c3670"></a>Chyba kompilátoru C3670

'override': nelze přepsat nepřístupnou základní třídu metoda "method"

Přepsání lze provádět pouze na funkce, jejichž úroveň přístupu je k dispozici v odvozeném typu. Další informace najdete v tématu [explicitní přepsání](../../windows/explicit-overrides-cpp-component-extensions.md).

Následující ukázka generuje C3670:

```
// C3670.cpp
// compile with: /clr /c
public ref class C {
// Uncomment the following line to resolve.
// public:
   virtual void g() { }
};

public ref class D : public C {
public:
   virtual void f() new sealed = C::g {};   // C3670
};
```