---
title: Chyba kompilátoru C2793
ms.date: 11/04/2016
f1_keywords:
- C2793
helpviewer_keywords:
- C2793
ms.assetid: ce35f4e8-c357-40ca-95c4-15ff001ad69d
ms.openlocfilehash: 5533a0e8f75a1a513fbabe451fb41629a4595382
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428181"
---
# <a name="compiler-error-c2793"></a>Chyba kompilátoru C2793

"token": Neočekávaný token za '::', identifikátor nebo klíčové slovo očekáván operátor

Pouze tokeny, pomocí kterých `__super::` se identifikátor nebo klíčové slovo `operator`.

Následující ukázka generuje C2793

```
// C2793.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super::(); // C2793
   }
};
```