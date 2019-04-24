---
title: Chyba kompilátoru C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 3f3fac9d5410595fe5653e257d97d2fd7c858545
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303486"
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