---
title: Chyba kompilátoru C2027 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2027
dev_langs:
- C++
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69aae289fbab56cd77e544118909b2d7ef72ae0c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032039"
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