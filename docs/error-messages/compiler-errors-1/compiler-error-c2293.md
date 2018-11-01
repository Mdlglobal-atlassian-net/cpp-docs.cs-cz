---
title: Chyba kompilátoru C2293
ms.date: 11/04/2016
f1_keywords:
- C2293
helpviewer_keywords:
- C2293
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
ms.openlocfilehash: 8073e952e8248367c444415cfb182743247dc6fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570635"
---
# <a name="compiler-error-c2293"></a>Chyba kompilátoru C2293

'identifier': neplatné mít členské proměnné jako specifikátor __based.

Specifikátory pro `__based` modifikátor musí být nečlenský ukazateli.

Následující ukázka generuje C2293:

```
// C2293.cpp
// compile with: /c
class A {
   static int *i;
   void __based(i) *bp;   // C2293
   void *bp2;   // OK
};
```