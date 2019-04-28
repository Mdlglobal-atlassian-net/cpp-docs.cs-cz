---
title: Kompilátor upozornění (úroveň 2) C4056
ms.date: 11/04/2016
f1_keywords:
- C4056
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
ms.openlocfilehash: 59c66f2f7dcbd1e20463df613b1b7deae6a1c349
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349864"
---
# <a name="compiler-warning-level-2-c4056"></a>Kompilátor upozornění (úroveň 2) C4056

přetečení v aritmetice plovoucí desetinné čárky konstanty

S plovoucí desetinnou čárkou aritmetice konstanty vygeneruje výsledek, který překračuje maximální povolenou hodnotu.

Toto upozornění může být způsobeno optimalizace kompilátoru během aritmetice konstanty. Můžete bezpečně ignorovat toto upozornění, pokud ho zmizí při vypnout optimalizaci ([/Od](../../build/reference/od-disable-debug.md)).

Následující ukázka generuje C4056:

```
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```