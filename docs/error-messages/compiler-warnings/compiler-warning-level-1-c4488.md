---
title: Kompilátor upozornění (úroveň 1) C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: c816c1b3f5481ccff19fd2a2377c5fc98f950fee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404075"
---
# <a name="compiler-warning-level-1-c4488"></a>Kompilátor upozornění (úroveň 1) C4488

'function': vyžaduje klíčové slovo '– klíčové slovo' o implementaci metody rozhraní "interface_method"

Třída musí implementovat všechny členy rozhraní, ze které přímo dědí. Implementovaný člen musí mít přístupnost public a musí být označena jako virtuální.

## <a name="example"></a>Příklad

C4488 může dojít, pokud implementovaný člen není veřejný. Následující ukázka generuje C4488.

```
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

## <a name="example"></a>Příklad

C4488 může dojít, pokud implementovaný člen není označený jako virtuální. Následující ukázka generuje C4488.

```
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```