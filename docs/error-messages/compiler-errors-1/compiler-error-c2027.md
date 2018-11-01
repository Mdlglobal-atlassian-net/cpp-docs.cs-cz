---
title: Chyba kompilátoru C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 3f3fac9d5410595fe5653e257d97d2fd7c858545
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446030"
---
# <a name="compiler-error-c2027"></a>Chyba kompilátoru C2027

použití nedefinovaného typu 'type'

Typ nelze použít, dokud je definována. Chcete-li vyřešit chybu, ujistěte se, že typ je plně definována před odkazování.

## <a name="example"></a>Příklad

Následující ukázka generuje C2027.

```
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

## <a name="example"></a>Příklad

Je možné deklarovat ukazatel na typ deklarovaný, ale nedefinovaná.  Ale jazyk Visual C++ neumožňuje odkaz na Nedefinovaný typ.

Následující ukázka generuje C2027.

```
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```