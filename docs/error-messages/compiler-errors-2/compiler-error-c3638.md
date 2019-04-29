---
title: Chyba kompilátoru C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: 33bb248faf946c39543de4a14a44e2ebbda49880
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385885"
---
# <a name="compiler-error-c3638"></a>Chyba kompilátoru C3638

'operator': nelze předefinovat standardní zabalení a rozbalení operátory převodu

Kompilátor definuje operátor převodu pro každé spravované třídy pro podporu implicitního zabalení. Tento operátor se nedá předefinovat.

Další informace najdete v tématu [implicitního zabalení](../../extensions/boxing-cpp-component-extensions.md).

Následující ukázka generuje C3638:

```
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