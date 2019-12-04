---
title: Chyba kompilátoru C3071
ms.date: 11/04/2016
f1_keywords:
- C3071
helpviewer_keywords:
- C3071
ms.assetid: 69879e66-a60e-4058-9bbd-d5c5e2d8ee37
ms.openlocfilehash: 26a95b18970aef450c6fdf718910aa3f816fd778
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759409"
---
# <a name="compiler-error-c3071"></a>Chyba kompilátoru C3071

operátor operator se dá použít jedině pro instanci ref class nebo Value-Type.

Operátor CLR nelze použít pro nativní typ. Operátor lze použít pro třídu ref class nebo ref struct (typ hodnoty), ale ne pro nativní typ, jako je například int nebo alias pro nativní typ, jako je například System:: Int32. Tyto typy nemohou být zabaleny C++ z kódu způsobem, který odkazuje na nativní proměnnou, takže operátor nelze použít.

Další informace naleznete v tématu [operátor sledování odkazů](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3071.

```cpp
// C3071.cpp
// compile with: /clr
class N {};
ref struct R {};

int main() {
   N n;
   %n;   // C3071

   R r;
   R ^ r2 = %r;   // OK
}
```
