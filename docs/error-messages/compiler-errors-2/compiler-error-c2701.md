---
title: Chyba kompilátoru C2701
ms.date: 11/04/2016
f1_keywords:
- C2701
helpviewer_keywords:
- C2701
ms.assetid: 31cf2ab7-ced9-4f75-aa51-e169e20407fb
ms.openlocfilehash: aabb47d3e0e2f494b19205626861dea43ca87033
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758330"
---
# <a name="compiler-error-c2701"></a>Chyba kompilátoru C2701

' function ': Šablona funkce nemůže být typu Friend lokální třídy

Lokální třída nemůže mít funkci šablony jako funkci Friend.

Následující ukázka generuje C2701:

```cpp
// C2701.cpp
// compile with: /c
template<typename T>   // OK
void f1(const T &);

void MyFunction() {
   class MyClass {
      template<typename T> friend void f2(const T &);   // C2701
   };
}
```
