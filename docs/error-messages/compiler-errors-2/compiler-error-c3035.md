---
title: Chyba kompilátoru C3035
ms.date: 11/04/2016
f1_keywords:
- C3035
helpviewer_keywords:
- C3035
ms.assetid: af34fad2-2b45-42d0-a9ff-04eab3e91c37
ms.openlocfilehash: e6d42c53407e1047d299e82566c7fadeb639641d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550511"
---
# <a name="compiler-error-c3035"></a>Chyba kompilátoru C3035

OpenMP – "řazení" musí mít směrnice vazbu přímo na 'pro' nebo parallel for s klauzulí ordered.

Klauzule seřazený byl chybně vytvořen.

Následující ukázka generuje C3035:

```
// C3035.cpp
// compile with: /openmp /link vcomps.lib
int main() {
   int n = 0, x, i;

   #pragma omp parallel private(n)
   {
      #pragma omp ordered   // C3035
      // Try the following line instead:
      // #pragma omp for ordered
       for (i = 0 ; i < 10 ; ++i)
         ;
   }
}
```