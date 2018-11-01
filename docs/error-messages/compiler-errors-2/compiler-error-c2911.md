---
title: Chyba kompilátoru C2911
ms.date: 11/04/2016
f1_keywords:
- C2911
helpviewer_keywords:
- C2911
ms.assetid: 83c7c01a-ab6a-4179-9fb0-289a9ec8d44e
ms.openlocfilehash: 56977f481a77c1f5865bec5d6ecc01c99d8224cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657259"
---
# <a name="compiler-error-c2911"></a>Chyba kompilátoru C2911

'member': nelze deklarovat nebo definovat v aktuálním rozsahu.

Uvnitř oboru názvů, třídy nebo funkce lze definovat pouze členy stejný obor názvů, třídy nebo funkce nebo člena, který je uzavřen ve stejný obor názvů, třídy nebo funkce.

Následující ukázka generuje C2911:

```
// C2911.cpp
struct A;

namespace M {
   struct D;
}

namespace N {
   struct C;

   namespace O {
      struct B;
   }

   // in N
   struct ::A {};   // C2911  A is member of global NS
   struct O::B{};   // OK B is in O, O is inside of N
   struct C {};     // OK C is member of N
   struct M::D {};  // C2911 D is member of M, M not enclosed by N
}
```