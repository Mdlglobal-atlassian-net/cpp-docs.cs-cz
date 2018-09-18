---
title: Chyba kompilátoru C3020 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3020
dev_langs:
- C++
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c7f86d116c1a830db54490f3e5231d837d4246c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060639"
---
# <a name="compiler-error-c3020"></a>Chyba kompilátoru C3020

'příkaz var': indexovaná proměnná OpenMP smyčku for nejde upravovat v těle smyčky

OpenMP `for` smyčky nesmíte upravovat indexu (čítače smyčky) v těle `for` smyčky.

Následující ukázka generuje C3020:

```
// C3020.cpp
// compile with: /openmp
int main() {
   int i = 0, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i += n)
         i *= 2;   // C3020
         // try the following line instead
         // n++;
   }
}
```

Proměnná deklarovaná pomocí [lastprivate](../../parallel/openmp/reference/lastprivate.md) nelze použít jako index uvnitř smyčka paralelizovaná.

Podle následující ukázky vám poskytne C3020 pro druhý lastprivate vzhledem k tomu, že lastprivate aktivují zápis do idx_a v krajních smyčky for. První lastprivate nedává chybu, protože tento lastprivate aktivuje zápis do idx_a mimo nejkrajnější pro smyčky (technicky vzato na konci velmi poslední iteraci). Následující ukázka generuje C3020.

```
// C3020b.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_a)   // C3020
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```

Následující příklad ukazuje možným řešením:

```
// C3020c.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_b)
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```