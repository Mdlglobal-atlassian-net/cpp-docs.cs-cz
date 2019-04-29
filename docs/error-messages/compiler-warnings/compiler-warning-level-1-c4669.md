---
title: Kompilátor upozornění (úroveň 1) C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: f4d0b87c91649c5f2f6b5823fea82d2ce355d11a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374596"
---
# <a name="compiler-warning-level-1-c4669"></a>Kompilátor upozornění (úroveň 1) C4669

'přetypovat': nebezpečný převod: 'class' je spravovaná nebo objekt typu WinRT

Přetypování obsahuje prostředí Windows Runtime nebo spravovaným typem. Kompilátor dokončení přetypování pomocí provádí bitové kopie jeden ukazatel do jiné, ale poskytuje žádné další kontrolu. Pokud chcete vyřešit toto upozornění, nepřetypujte třídy obsahující spravované členy a typy Windows Runtime.

Následující ukázka generuje C4669 a ukazuje, jak ho opravit:

```
// C4669.cpp
// compile with: /clr /W1
ref struct A {
   int i;
   Object ^ pObj;   // remove the managed member to fix the warning
};

ref struct B {
   int j;
};

int main() {
   A ^ a = gcnew A;
   B ^ b = reinterpret_cast<B ^>(a);   // C4669
}
```