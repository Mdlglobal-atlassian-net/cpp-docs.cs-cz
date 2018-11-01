---
title: Chyba kompilátoru C2041
ms.date: 11/04/2016
f1_keywords:
- C2041
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
ms.openlocfilehash: 37d32285f9c01efb981c5f02acba21f2d6fe3dc2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593502"
---
# <a name="compiler-error-c2041"></a>Chyba kompilátoru C2041

Neplatná číslice "znak" základní "číslo"

Zadaný znak není platnou číslici pro základní (například osmičkové nebo šestnáctkové).

Následující ukázka generuje C2041:

```
// C2041.cpp
int i = 081;   // C2041  8 is not a base 8 digit
```

Možná řešení:

```
// C2041b.cpp
// compile with: /c
int j = 071;
```