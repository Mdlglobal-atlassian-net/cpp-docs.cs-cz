---
title: Kompilátor upozornění (úroveň 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 1c92bd7f632ea6662c3cee1bcaa1dd0c917fb2a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661302"
---
# <a name="compiler-warning-level-3-c4570"></a>Kompilátor upozornění (úroveň 3) C4570

'type': není explicitně deklarované jako abstraktní, ale má abstraktní funkce

Typ, který obsahuje [abstraktní](../../windows/abstract-cpp-component-extensions.md) funkce by měla být označena jako abstraktní.

## <a name="example"></a>Příklad

Následující ukázka generuje C4570.

```
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```