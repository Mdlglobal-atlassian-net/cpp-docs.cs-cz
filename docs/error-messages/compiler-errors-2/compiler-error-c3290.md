---
title: Chyba kompilátoru C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: d82d3272563f7a5af5de399a2f7fff621500e612
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490477"
---
# <a name="compiler-error-c3290"></a>Chyba kompilátoru C3290

'type': triviální vlastnost nemůže mít odkazový typ.

Vlastnost byl deklarován nesprávně. Když deklarujete triviální vlastnost, kompilátor vytvoří proměnnou, která aktualizuje vlastnost a není možné mít sledovací odkaz proměnnou v třídě.

Zobrazit [vlastnost](../../windows/property-cpp-component-extensions.md) a [Tracking Reference Operator](../../windows/tracking-reference-operator-cpp-component-extensions.md) Další informace.

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