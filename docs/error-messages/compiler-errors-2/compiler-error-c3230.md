---
title: Chyba kompilátoru C3230
ms.date: 11/04/2016
f1_keywords:
- C3230
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
ms.openlocfilehash: a4d5edeb5898a57b99839b7e044f909cea1ec199
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428246"
---
# <a name="compiler-error-c3230"></a>Chyba kompilátoru C3230

'function': argument typu šablony pro "Šablona" nemůže obsahovat parametr obecného typu: 'param'

Šablony jsou vytvořeny v době kompilace, ale instance se vytvářejí obecné typy v době běhu. Proto není možné generovat obecný kód, který lze volat šablony, protože šablona se nedá vytvořit instance v době běhu, když se nakonec označuje obecného typu.

Následující ukázka generuje C3230:

```
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