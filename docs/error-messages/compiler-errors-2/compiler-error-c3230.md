---
title: Chyba kompilátoru C3230
ms.date: 11/04/2016
f1_keywords:
- C3230
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
ms.openlocfilehash: 69ea279ac5e11c03f366711484ba0c250fc50225
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743312"
---
# <a name="compiler-error-c3230"></a>Chyba kompilátoru C3230

' function ': argument typu šablony pro ' Template ' nemůže obsahovat parametr obecného typu: ' param '

Šablony jsou vytvořeny v době kompilace, ale obecné jsou vytvořeny v době běhu. Proto není možné generovat obecný kód, který může zavolat šablonu, protože šablonu nelze vytvořit za běhu, když je obecný typ nakonec znám.

Následující ukázka generuje C3230:

```cpp
// C3230.cpp
// compile with: /clr /LD
template <class S>
void f(S t);

generic <class U>
ref class C {
   void f1(U x) {
      f(x);   // C3230
   }
};
```
