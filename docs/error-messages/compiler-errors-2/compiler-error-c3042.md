---
title: Chyba kompilátoru C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: deb3b8d6251316bceb71ce03f2bda88520bbb9b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182584"
---
# <a name="compiler-error-c3042"></a>Chyba kompilátoru C3042

"copyprivate" a 'nowait' nemůžou být společně v direktivě OpenMP "direktiva"

[Copyprivate](../../parallel/openmp/reference/copyprivate.md) a [nowait](../../parallel/openmp/reference/nowait.md) klauzule se vzájemně vylučují pro zadaný direktivu. Chcete-li tuto chybu opravit, odebrat jedno nebo obě `copyprivate` nebo `nowait` klauzule.

Následující ukázka generuje C3042:

```
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