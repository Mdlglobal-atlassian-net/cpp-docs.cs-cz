---
title: Chyba kompilátoru C2082
ms.date: 11/04/2016
f1_keywords:
- C2082
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
ms.openlocfilehash: 754a079a152fd3aeaf4da4e27633a4a3476a8959
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757706"
---
# <a name="compiler-error-c2082"></a>Chyba kompilátoru C2082

předefinování formálního parametru Identifier

Formální parametr funkce je znovu deklarován v těle funkce. Chcete-li chybu vyřešit, odeberte předefinování.

Následující ukázka generuje C2082:

```cpp
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```
