---
title: Upozornění kompilátoru (úroveň 4) C4938
ms.date: 11/04/2016
f1_keywords:
- C4938
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
ms.openlocfilehash: c752b5daea42eac7c7dd0e14581d9e781aac9c96
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988733"
---
# <a name="compiler-warning-level-4-c4938"></a>Upozornění kompilátoru (úroveň 4) C4938

var: proměnlivé omezení desetinné čárky může způsobit nekonzistentní výsledky v/FP: Strict nebo #pragma fenv_access

Neměli byste používat [/FP: Strict](../../build/reference/fp-specify-floating-point-behavior.md) nebo [fenv_access](../../preprocessor/fenv-access.md) s snížením hodnot OpenMP s plovoucí desetinnou čárkou, protože součet je vypočítáván v jiném pořadí. Proto se výsledky můžou lišit od výsledků bez/OpenMP.

Následující ukázka generuje C4938:

```cpp
// C4938.cpp
// compile with: /openmp /W4 /fp:strict /c
// #pragma fenv_access(on)
extern double *a;

double test(int first, int last) {
   double sum = 0.0;
   #pragma omp parallel for reduction(+: sum)   // C4938
   for (int i = first ; i <= last ; ++i)
      sum += a[i];
   return sum;
}
```

Bez explicitního paralelismu se součet vypočítá takto:

```
sum = a[first] + a[first + 1] + ... + a[last];
```

V případě explicitního paralelismu (a dvou vláken) se součet vypočítá takto:

```
sum1 = a[first] + ... a[first + last / 2];
sum2 = a[(first + last / 2) + 1] + ... a[last];
sum = sum1 + sum2;
```
