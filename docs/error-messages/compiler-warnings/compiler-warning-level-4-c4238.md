---
title: Kompilátor upozornění (úroveň 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: c5ffa07b06f010d10edc14aa7576bb614aa9dd04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471900"
---
# <a name="compiler-warning-level-4-c4238"></a>Kompilátor upozornění (úroveň 4) C4238

používá se nestandardní rozšíření: rvalue třídy se používá jako l-hodnoty.

Z důvodu kompatibility s předchozími verzemi sady Visual C++, rozšíření společnosti Microsoft (**/Ze**) vám umožní použít typ třídy jako r-hodnoty. v kontextu, který implicitně nebo explicitně přijímá jeho adresu. V některých případech, například v příkladu níže to může být nebezpečné.

## <a name="example"></a>Příklad

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Toto použití způsobí chybu podle kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).