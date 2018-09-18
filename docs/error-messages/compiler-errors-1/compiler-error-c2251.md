---
title: Chyba kompilátoru C2251 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2251
dev_langs:
- C++
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62e27fd7c028e059aa04cc3ff9f4b278cd1a120e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048289"
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