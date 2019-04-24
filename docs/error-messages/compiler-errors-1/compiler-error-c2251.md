---
title: Chyba kompilátoru C2251
ms.date: 11/04/2016
f1_keywords:
- C2251
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
ms.openlocfilehash: b7ffb5b8d425e74523e491827ffb8878b8e03b38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301380"
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