---
title: Chyba kompilátoru C3417
ms.date: 11/04/2016
f1_keywords:
- C3417
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
ms.openlocfilehash: 574af940f17c1a79472d6d20d63c9ff74d4c411e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615761"
---
# <a name="compiler-error-c3417"></a>Chyba kompilátoru C3417

'member': hodnotové typy nemůžou obsahovat speciální členské funkce definované uživatele

Hodnotové typy nemůžou obsahovat funkce, jako je výchozí konstruktor instance, destruktor nebo kopírovací konstruktor.

Následující ukázka generuje C3517:

```
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```