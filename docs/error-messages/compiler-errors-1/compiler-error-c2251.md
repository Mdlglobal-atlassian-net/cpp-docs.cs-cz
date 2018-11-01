---
title: Chyba kompilátoru C2251
ms.date: 11/04/2016
f1_keywords:
- C2251
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
ms.openlocfilehash: b7ffb5b8d425e74523e491827ffb8878b8e03b38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452335"
---
# <a name="compiler-error-c2251"></a>Chyba kompilátoru C2251

obor názvů 'obor názvů' nemá člena 'member' - měli jste na mysli 'member'?

Kompilátor se nepodařilo najít identifikátor v určeném oboru názvů.

Následující ukázka generuje C2251:

```
// C2251.cpp
// compile with: /c
namespace A {
   namespace B {
      void f1();
   }

   using namespace B;
}

void A::f1() {}   // C2251
void A::B::f1() {}   // OK
```