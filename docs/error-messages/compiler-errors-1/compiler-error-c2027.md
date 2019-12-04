---
title: Chyba kompilátoru C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 62cf208d9d0025afba06d32a15b9a1e50777c473
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750998"
---
# <a name="compiler-error-c2027"></a>Chyba kompilátoru C2027

použití nedefinovaného typu typu

Typ nelze použít, dokud není definován. Chcete-li chybu vyřešit, ujistěte se, že je typ zcela definován před odkazem na něj.

## <a name="example"></a>Příklad

Následující ukázka generuje C2027.

```cpp
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

Je možné deklarovat ukazatel na deklarovaný, ale Nedefinovaný typ. Ale C++ nepovoluje odkaz na Nedefinovaný typ.

Následující ukázka generuje C2027.

```cpp
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
