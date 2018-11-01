---
title: Chyba kompilátoru C2213
ms.date: 11/04/2016
f1_keywords:
- C2213
helpviewer_keywords:
- C2213
ms.assetid: ff012278-7f3b-4d49-aaed-2349756f6225
ms.openlocfilehash: 125529aa23d43d9acd63652f73f636fee567f90a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433440"
---
# <a name="compiler-error-c2213"></a>Chyba kompilátoru C2213

'modifikátor': Neplatný argument __based

Změna argumentu `__based` je neplatný.

Následující ukázka generuje C2213:

```
// C2213.cpp
// compile with: /c
int i;
int *j;
char __based(i) *p;   // C2213
char __based(j) *p2;   // OK
```