---
title: Chyba kompilátoru C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: a8fe0802a7529551fce1c0b7242c867db52d8842
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756757"
---
# <a name="compiler-error-c3072"></a>Chyba kompilátoru C3072

operátor operator nelze použít na instanci třídy ref.

Použijte unární operátor`operator` k převedení instance třídy ref class na typ popisovače.

Typ CLR vyžaduje operátory CLR, nikoli nativní operátory (nebo standardní).  Další informace naleznete v tématu [operátor sledování odkazů](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3072.

```cpp
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
