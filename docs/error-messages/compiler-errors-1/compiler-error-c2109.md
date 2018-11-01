---
title: Chyba kompilátoru C2109
ms.date: 11/04/2016
f1_keywords:
- C2109
helpviewer_keywords:
- C2109
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
ms.openlocfilehash: 6592f36b29fe643e088669089b1af1b69b7b2125
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452049"
---
# <a name="compiler-error-c2109"></a>Chyba kompilátoru C2109

Subscript vyžaduje typ pole nebo ukazatel

Dolního indexu byla použita na proměnnou, která není pole.

Následující ukázka generuje C2109:

```
// C2109.cpp
int main() {
   int a, b[10] = {0};
   a[0] = 1;   // C2109
   b[0] = 1;   // OK
}
```