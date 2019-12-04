---
title: Chyba kompilátoru C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: 9054124cbfe2d86c062c6e97651bd69eebe5471c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748746"
---
# <a name="compiler-error-c3912"></a>Chyba kompilátoru C3912

' Event ': typ události musí být delegovaný typ.

Událost byla deklarována, ale nebyla správného typu.

Další informace najdete v tématu [událost](../../extensions/event-cpp-component-extensions.md).

Následující ukázka generuje C3912:

```cpp
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```
