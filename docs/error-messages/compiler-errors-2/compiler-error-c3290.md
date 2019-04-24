---
title: Compiler Error C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: f2a346354d8da7d78c5517b01b4438bfb8af50ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222704"
---
# <a name="compiler-error-c3290"></a>Compiler Error C3290

'type': triviální vlastnost nemůže mít odkazový typ.

Vlastnost byl deklarován nesprávně. Když deklarujete triviální vlastnost, kompilátor vytvoří proměnnou, která aktualizuje vlastnost a není možné mít sledovací odkaz proměnnou v třídě.

Zobrazit [vlastnost](../../extensions/property-cpp-component-extensions.md) a [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3290.

```
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