---
title: Chyba kompilátoru C2931
ms.date: 11/04/2016
f1_keywords:
- C2931
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
ms.openlocfilehash: 03c5c1865343afdc0fd7a67ce393c7e1a5d2966f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757693"
---
# <a name="compiler-error-c2931"></a>Chyba kompilátoru C2931

' class ': typ-class-ID se předefinovalo jako členská funkce ' identifier '

Nelze použít obecnou třídu nebo třídu šablony jako členskou funkci jiné třídy.

Tato chyba může být způsobena nesprávným spárováním složených závorek.

Následující ukázka generuje C2931:

```cpp
// C2931.cpp
// compile with: /c
template<class T>
struct TC { };
struct MyStruct {
   void TC<int>();   // C2931
};

struct TC2 { };
struct MyStruct2 {
   void TC2();
};
```

C2931 může také nastat při použití generických typů:

```cpp
// C2931b.cpp
// compile with: /clr /c
generic<class T> ref struct GC {};
struct MyStruct {
   void GC<int>();   // C2931
   void GC2();   // OK
};
```
