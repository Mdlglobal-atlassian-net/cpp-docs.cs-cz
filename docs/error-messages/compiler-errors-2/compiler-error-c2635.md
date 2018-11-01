---
title: Chyba kompilátoru C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 0c31bcc4062aec1d939c801f9b5ee420f2f4fcb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468117"
---
# <a name="compiler-error-c2635"></a>Chyba kompilátoru C2635

nelze převést "identifier1 *" "identifier2\*'; implicitní převod z virtuální základní třídy

Převod vyžaduje přetypování z typu `virtual` základní třídy na odvozenou třídu, která není povolena.

Následující ukázka generuje C2635:

```
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```