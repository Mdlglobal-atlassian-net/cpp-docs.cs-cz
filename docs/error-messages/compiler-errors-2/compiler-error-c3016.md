---
title: Chyba kompilátoru C3016
ms.date: 11/04/2016
f1_keywords:
- C3016
helpviewer_keywords:
- C3016
ms.assetid: 3423467e-e8bb-4f35-b4db-7925cafa74c1
ms.openlocfilehash: edb83c210ca7e3f6c648522b893e9ed90cea1874
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479648"
---
# <a name="compiler-error-c3016"></a>Chyba kompilátoru C3016

'příkaz var': indexovaná proměnná příkazu for v OpenMP musí mít celočíselný typ se znaménkem

Indexovaná proměnná v OpenMP `for` příkaz musí být celočíselný typ se znaménkem.

Následující ukázka generuje C3016:

```
// C3016.cpp
// compile with: /openmp
int main()
{
   #pragma omp parallel
   {
      unsigned int i = 0;
      // Try the following line instead:
      // int i = 0;

      #pragma omp for
      for (i = 0; i <= 10; ++i)   // C3016
      {
      }
   }
}
```