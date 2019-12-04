---
title: Chyba kompilátoru C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: a7a73c13c28923761674294d8d6e601b95ffad96
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760150"
---
# <a name="compiler-error-c3290"></a>Chyba kompilátoru C3290

Typ: triviální vlastnost nemůže mít odkazový typ.

Vlastnost byla deklarována nesprávně. Pokud deklarujete triviální vlastnost, kompilátor vytvoří proměnnou, kterou bude vlastnost aktualizovat, a není možné mít sledovací proměnnou reference ve třídě.

Další informace najdete v tématu o [vlastnostech](../../extensions/property-cpp-component-extensions.md) a [operátorovi sledování odkazů](../../extensions/tracking-reference-operator-cpp-component-extensions.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C3290.

```cpp
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```
