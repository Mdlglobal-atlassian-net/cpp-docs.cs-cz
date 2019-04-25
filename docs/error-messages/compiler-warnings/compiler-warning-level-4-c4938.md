---
title: Kompilátor upozornění (úroveň 4) C4938
ms.date: 11/04/2016
f1_keywords:
- C4938
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
ms.openlocfilehash: da2725a398a99b5943e128038e75622115a9e34f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280201"
---
# <a name="compiler-warning-level-4-c4938"></a>Kompilátor upozornění (úroveň 4) C4938

příkaz 'var': Plovoucího bodu redukční proměnná může způsobit nekonzistentní výsledky v/FP: strict nebo #pragma fenv_access

Neměli byste používat [/FP: strict](../../build/reference/fp-specify-floating-point-behavior.md) nebo [fenv_access](../../preprocessor/fenv-access.md) s OpenMP snížení s plovoucí desetinnou čárkou, protože součet je vypočítán v jiném pořadí. Výsledky se díky tomu se může lišit od výsledky bez/OpenMP.

Následující ukázka generuje C4938:

```
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

Bez explicitní paralelizace součet vypočítat následujícím způsobem:

```
sum = a[first] + a[first + 1] + ... + a[last];
```

Explicitní paralelizace (a dvěma vlákny) součet vypočítat následujícím způsobem:

```
sum1 = a[first] + ... a[first + last / 2];
sum2 = a[(first + last / 2) + 1] + ... a[last];
sum = sum1 + sum2;
```