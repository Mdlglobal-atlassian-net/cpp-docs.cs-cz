---
title: Chyba kompilátoru C3042 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3042
dev_langs:
- C++
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36fde6251244582a0626c80aa673ed6dd0e559d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045214"
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