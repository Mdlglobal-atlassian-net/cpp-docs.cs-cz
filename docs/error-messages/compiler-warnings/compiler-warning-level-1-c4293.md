---
title: Kompilátor upozornění (úroveň 1) C4293
ms.date: 11/04/2016
f1_keywords:
- C4293
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
ms.openlocfilehash: 03520e2018efd611985c0eeca8bb2cac259ff3cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598520"
---
# <a name="compiler-warning-level-1-c4293"></a>Kompilátor upozornění (úroveň 1) C4293

'operator': záporný nebo moc velký počet operací shift je; nedefinované chování

Pokud počet posunů je záporný nebo moc velký, bude výsledkem obraz chování není definováno.

## <a name="example"></a>Příklad

Následující ukázka generuje C4293:

```
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi) {

   return (hi << 32) | lo;   // C4293

   // try the following line instead
   // return ( (unsigned __int64)hi << 32) | lo;
}
```