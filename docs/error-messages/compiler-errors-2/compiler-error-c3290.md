---
title: Chyba kompilátoru C3290 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3290
dev_langs:
- C++
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b97818dd6ef7b38bb815e2c0a6345cc056fc45c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058923"
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