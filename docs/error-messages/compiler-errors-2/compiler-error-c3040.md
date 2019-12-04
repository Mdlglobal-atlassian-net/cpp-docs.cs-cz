---
title: Chyba kompilátoru C3040
ms.date: 11/04/2016
f1_keywords:
- C3040
helpviewer_keywords:
- C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
ms.openlocfilehash: 8a7ee7b814be1963e2d98b54e547cc5965eef9d3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754950"
---
# <a name="compiler-error-c3040"></a>Chyba kompilátoru C3040

var: typ proměnné v klauzuli Reduction není kompatibilní s operátorem Reduction operator.

Proměnnou v klauzuli [Reduction](../../parallel/openmp/reference/reduction.md) nelze použít s operátorem Reduction.

Následující ukázka generuje C3040:

```cpp
// C3040.cpp
// compile with: /openmp /c
#include "omp.h"
double d;

int main() {
   #pragma omp parallel reduction(&:d)   // C3040
      ;

   #pragma omp parallel reduction(-:d)  // OK
      ;
}
```
