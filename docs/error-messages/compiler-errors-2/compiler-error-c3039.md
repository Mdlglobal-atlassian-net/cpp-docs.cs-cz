---
title: Chyba kompilátoru C3039
ms.date: 11/04/2016
f1_keywords:
- C3039
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
ms.openlocfilehash: 69be1b25254119108e517cee2f1e14368e0163f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511615"
---
# <a name="compiler-error-c3039"></a>Chyba kompilátoru C3039

'příkaz var': indexovaná proměnná v OpenMP for – příkaz nemůže být redukční proměnná

Indexovaná proměnná je implicitně soukromé, tak proměnnou nelze použít v [snížení](../../parallel/openmp/reference/reduction.md) klauzule nadřazený [paralelní](../../parallel/openmp/reference/parallel.md) směrnice.

## <a name="example"></a>Příklad

Následující ukázka generuje C3039:

```
// C3039.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel reduction(+: i)
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // C3039
         g_i += i;
   }
}
```