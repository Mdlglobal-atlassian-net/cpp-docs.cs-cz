---
title: Chyba kompilátoru C2386
ms.date: 11/04/2016
f1_keywords:
- C2386
helpviewer_keywords:
- C2386
ms.assetid: aaaa1284-34a0-4da2-8547-9fcbb559dae0
ms.openlocfilehash: a75ccd9824106f2b954cd090a0e00ab11786d243
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667655"
---
# <a name="compiler-error-c2386"></a>Chyba kompilátoru C2386

'symbol': symbol s tímto názvem již existuje v aktuálním rozsahu.

Pokusili jste se vytvořit alias oboru názvů, ale název, který jste zvolili, již existuje.

Následující ukázka generuje C2386:

```
// C2386.cpp
namespace A {
   int k;
}

int i;
namespace i = A;   // C2386, i already exists
```