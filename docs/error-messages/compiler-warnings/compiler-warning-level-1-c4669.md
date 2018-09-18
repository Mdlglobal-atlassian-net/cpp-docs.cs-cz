---
title: Upozornění (úroveň 1) C4669 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4669
dev_langs:
- C++
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f96bcf40b1fbc989daceabc810d019d1bb9aa98
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060850"
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