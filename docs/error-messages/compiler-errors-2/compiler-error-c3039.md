---
title: Chyba kompilátoru C3039
ms.date: 11/04/2016
f1_keywords:
- C3039
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
ms.openlocfilehash: 344fd32e66881c2529ddb1f9185c25752f0a736c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754976"
---
# <a name="compiler-error-c3039"></a>Chyba kompilátoru C3039

var: indexová proměnná v příkazu OpenMP for nemůže být redukční proměnná.

Proměnná indexu je implicitně soukromá, takže proměnnou nelze použít v klauzuli [Reduction](../../parallel/openmp/reference/reduction.md) v nadřazené [paralelní](../../parallel/openmp/reference/parallel.md) direktivě.

## <a name="example"></a>Příklad

Následující ukázka generuje C3039:

```cpp
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
