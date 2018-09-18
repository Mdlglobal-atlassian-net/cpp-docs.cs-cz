---
title: Upozornění (úroveň 2) C4056 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4056
dev_langs:
- C++
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e069867d4aef749f9f6e42f46a34745d9e8aa62
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067504"
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