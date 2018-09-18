---
title: Upozornění (úroveň 4) C4938 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4938
dev_langs:
- C++
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e140f3885aec66d01d5f7e28245c10e952bedde3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107439"
---
# <a name="compiler-warning-level-4-c4938"></a>Kompilátor upozornění (úroveň 4) C4938

'příkaz var': plovoucího bodu redukční proměnná může způsobit nekonzistentní výsledky v/FP: strict nebo #pragma fenv_access

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