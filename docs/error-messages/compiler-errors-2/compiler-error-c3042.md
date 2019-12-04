---
title: Chyba kompilátoru C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: 4347e5ee0e61ada700082b4954b616ce894e57b9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761387"
---
# <a name="compiler-error-c3042"></a>Chyba kompilátoru C3042

klauzule copyprivate a New Wait se nemůžou vyskytovat společně s direktivou OpenMP direktivy.

Klauzule [copyprivate](../../parallel/openmp/reference/copyprivate.md) a [Wait](../../parallel/openmp/reference/nowait.md) se vzájemně vylučují na zadané direktivě. Chcete-li tuto chybu opravit, odeberte jednu nebo obě klauzule `copyprivate` nebo `nowait`.

Následující ukázka generuje C3042:

```cpp
// C3042.cpp
// compile with: /openmp /c
#include <stdio.h>
#include "omp.h"

double d;

int main() {
    #pragma omp parallel private(d)
   {
      #pragma omp single copyprivate(d) nowait   // C3042
      {
      }
   }
}
```
