---
title: Chyba kompilátoru C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: 15f9ba62751d9b3cb17ab56659310292dab41adf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596778"
---
# <a name="compiler-error-c2588"></a>Chyba kompilátoru C2588

':: ~ identifikátor ': Neplatná globální – destruktor

Destruktor je definována pro něco jiného než třída, struktura nebo sjednocení. Toto není povoleno.

Tuto chybu může způsobovat chybějící třídy, struktury nebo sjednocení název na levé straně rozlišení oboru (`::`) – operátor.

Následující ukázka generuje C2588:

```
// C2588.cpp
~F();   // C2588
```