---
title: Kompilátor upozornění (úroveň 4) C4937
ms.date: 11/04/2016
f1_keywords:
- C4937
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
ms.openlocfilehash: 64565ad37c965aa0af3b912988586b37270be6a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548752"
---
# <a name="compiler-warning-level-4-c4937"></a>Kompilátor upozornění (úroveň 4) C4937

"text1" a "text2" jsou nejde rozlišit jako argumenty 'direktivy.

Vzhledem ke způsobu zpracování argumentů direktivy, názvy, které mají význam pro kompilátor, jako jsou klíčová slova s více reprezentací text (jednoduché nebo dvojité podtržítka formuláře), nemůže být rozlišující kompilátorem.

Příkladem takových řetězce jsou __cdecl a \__forceinline.  Mějte na paměti, v části /Za, že jsou povoleny pouze formulářů dvojitým podtržítkem.

Následující ukázka generuje C4937:

```
// C4937.cpp
// compile with: /openmp /W4
#include "omp.h"
int main() {
   #pragma omp critical ( __leave )   // C4937
   ;

   // OK
   #pragma omp critical ( leave )
   ;
}
```