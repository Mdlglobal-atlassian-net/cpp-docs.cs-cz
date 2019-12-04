---
title: Chyba kompilátoru C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: f8d67ac0ff6a1fa5d9efbb8d85747ff94d75c648
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742493"
---
# <a name="compiler-error-c3638"></a>Chyba kompilátoru C3638

' operator ': operátory převodu standardního zabalení a rozbalení nelze předefinovat

Kompilátor definuje operátor převodu pro každou spravovanou třídu pro podporu implicitního zabalení. Tento operátor nelze předefinovat.

Další informace naleznete v tématu [implicitní zabalení](../../extensions/boxing-cpp-component-extensions.md).

Následující ukázka generuje C3638:

```cpp
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```
