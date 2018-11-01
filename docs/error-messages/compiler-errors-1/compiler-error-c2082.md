---
title: Chyba kompilátoru C2082
ms.date: 11/04/2016
f1_keywords:
- C2082
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
ms.openlocfilehash: 8bfb54dc91ef9132e3930e2c0799070f80f5cd0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577252"
---
# <a name="compiler-error-c2082"></a>Chyba kompilátoru C2082

Předefinování formálního parametru 'identifier'

Formální parametr funkce je deklarováno v rámci těla funkce. Chcete-li chybu vyřešit, odeberte Změna definice.

Následující ukázka generuje C2082:

```
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```