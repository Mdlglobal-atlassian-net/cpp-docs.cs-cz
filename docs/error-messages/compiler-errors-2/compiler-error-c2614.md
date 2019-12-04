---
title: Chyba kompilátoru C2614
ms.date: 11/04/2016
f1_keywords:
- C2614
helpviewer_keywords:
- C2614
ms.assetid: a550c1d5-8718-4e17-a888-b2619e00fe11
ms.openlocfilehash: 202d7f4caec3aabfde5d69adeaafa3da5dd67623
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737670"
---
# <a name="compiler-error-c2614"></a>Chyba kompilátoru C2614

' Class1 ': Neplatná inicializace členu: ' Class2 ' není základem nebo členem

V seznamu inicializace pro třídu nebo strukturu mohou být zobrazeny pouze členské nebo základní třídy.

## <a name="example"></a>Příklad

Následující ukázka generuje C2614.

```cpp
// C2614.cpp
// compile with: /c
struct A {
   int i;
   A( int ia ) : B( i ) {};   // C2614 B is not a member of A
};

struct A2 {
   int B;
   int i;
   A2( int ia ) : B( i ) {};   // OK
};
```
