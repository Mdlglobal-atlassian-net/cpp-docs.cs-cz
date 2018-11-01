---
title: Chyba kompilátoru C3231
ms.date: 11/04/2016
f1_keywords:
- C3231
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
ms.openlocfilehash: 653f0b18737f937483f5d3e79cb99c9a55160c19
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571961"
---
# <a name="compiler-error-c3231"></a>Chyba kompilátoru C3231

'arg': argument typu šablony nelze použít parametr obecného typu

Šablony jsou vytvořeny v době kompilace, ale instance se vytvářejí obecné typy v době běhu. Proto není možné generovat obecný kód, který lze volat šablony, protože šablona se nedá vytvořit instance v době běhu, když se nakonec označuje obecného typu.

Následující ukázka generuje C3231:

```
// C3231.cpp
// compile with: /clr /LD
template <class T> class A;

generic <class T>
ref class C {
   void f() {
      A<T> a;   // C3231
   }
};
```