---
title: Chyba kompilátoru C3022
ms.date: 11/04/2016
f1_keywords:
- C3022
helpviewer_keywords:
- C3022
ms.assetid: 9f1d444c-6c6e-48d9-9346-69128390aa33
ms.openlocfilehash: 187db5a7150ee0956258e83596966e269e5e50c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360096"
---
# <a name="compiler-error-c3022"></a>Chyba kompilátoru C3022

'klauzule': Neplatný typ plánu "hodnota" na "direktiva" OpenMP – direktiva

Nepodporovaná hodnota byl předán klauzuli.

Následující ukázka generuje C3022:

```
// C3022.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main() {
   int i;

   #pragma omp parallel for schedule(10)   // C3022
   for (i = 0; i < 10; ++i) ;

   #pragma omp parallel for schedule(x)   // C3022
   for (i = 0; i < 10; ++i) ;

   // OK
   #pragma omp parallel for schedule(runtime)
   for (i = 0; i < 10; ++i)
   ;
}
```