---
title: Chyba kompilátoru C3671
ms.date: 11/04/2016
f1_keywords:
- C3671
helpviewer_keywords:
- C3671
ms.assetid: d684e4ae-87e2-4424-80bb-6f346652c831
ms.openlocfilehash: 030a6acb19c0907956d2a5b833b683821591e5c5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758109"
---
# <a name="compiler-error-c3671"></a>Chyba kompilátoru C3671

' function_1 ': funkce nepřepisuje ' function_2 '

Při použití explicitní syntaxe přepsání kompilátor vygeneruje chybu, pokud funkce není přepsána.  Další informace najdete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C3671.

```cpp
// C3671.cpp
// compile with: /clr /c
ref struct S {
   virtual void f();
};

ref struct S1 : S {
   virtual void f(int) new sealed = S::f;   // C3671
   virtual void f() new sealed = S::f;
};
```
