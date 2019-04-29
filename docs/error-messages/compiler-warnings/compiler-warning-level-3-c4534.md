---
title: Kompilátor upozornění (úroveň 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 81445ff42aca78a8e40e9c88eff4bb76a41a8669
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401875"
---
# <a name="compiler-warning-level-3-c4534"></a>Kompilátor upozornění (úroveň 3) C4534

"konstruktoru" nesmí být výchozí konstruktor pro třídu 'class' z důvodu výchozího argumentu

Nespravovaná třída může mít konstruktor s parametry, které mají výchozí hodnoty a kompilátor bude použít jako výchozí konstruktor. Třída označena `value` – klíčové slovo nebudeme používat konstruktor s použitím výchozích hodnot pro parametry jako výchozí konstruktor.

Další informace najdete v tématu [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md).

Následující ukázka generuje C4534:

```
// C4534.cpp
// compile with: /W3 /clr /WX
value class MyClass {
public:
   int ii;
   MyClass(int i = 9) {   // C4534, will not be the default constructor
      i++;
   }
};

int main() {
   MyClass ^ xx = gcnew MyClass;
   xx->ii = 0;
}
```