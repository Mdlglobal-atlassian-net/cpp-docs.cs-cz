---
title: Upozornění kompilátoru (úroveň 1) C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: b45490ec399249a721f2d2567ca0182d44667243
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175556"
---
# <a name="compiler-warning-level-1-c4669"></a>Upozornění kompilátoru (úroveň 1) C4669

cast: nebezpečný převod: Class je typ spravovaného nebo WinRTového objektu.

Přetypování obsahuje prostředí Windows Runtime nebo spravovaný typ. Kompilátor dokončí přetypování provedením bitové kopie jednoho ukazatele na druhý, ale neposkytuje žádnou jinou kontrolu. Chcete-li vyřešit toto upozornění, Nepřetypujte třídy obsahující spravované členy nebo prostředí Windows Runtime typy.

Následující ukázka generuje C4669 a ukazuje, jak ji opravit:

```cpp
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
