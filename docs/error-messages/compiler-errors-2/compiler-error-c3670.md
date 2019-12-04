---
title: Chyba kompilátoru C3670
ms.date: 11/04/2016
f1_keywords:
- C3670
helpviewer_keywords:
- C3670
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
ms.openlocfilehash: 1b52f58f47027d88d9b0e150ebd2bf4588161553
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758122"
---
# <a name="compiler-error-c3670"></a>Chyba kompilátoru C3670

override: nejde přepsat nepřístupnou metodu základní třídy Method.

Přepsání může probíhat pouze na funkci, jejíž úroveň přístupu je k dispozici v odvozeném typu. Další informace najdete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

Následující ukázka generuje C3670:

```cpp
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
