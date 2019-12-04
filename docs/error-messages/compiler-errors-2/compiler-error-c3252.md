---
title: Chyba kompilátoru C3252
ms.date: 11/04/2016
f1_keywords:
- C3252
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
ms.openlocfilehash: fbfe3ffaca66cad4922b5771ee8c9003acba7571
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754326"
---
# <a name="compiler-error-c3252"></a>Chyba kompilátoru C3252

' Method ': nejde snížit přístupnost virtuální metody ve spravovaném nebo WinRT typu.

Třída, která implementuje virtuální metodu ze základní třídy nebo jakékoli metody z rozhraní, nemůže snížit přístup k této metodě.

Všimněte si, že všechny metody v rozhraní jsou veřejné.

Následující ukázka generuje C3252 a ukazuje, jak ji opravit:

```cpp
// C3252.cpp
// compile with: /clr /c
ref class A {
public:
   virtual void f1() {}
};

ref class B : public A {
// To fix, uncomment the following line:
// public:
   virtual void f1() override sealed {}   // C3252, make this method public
};
```
