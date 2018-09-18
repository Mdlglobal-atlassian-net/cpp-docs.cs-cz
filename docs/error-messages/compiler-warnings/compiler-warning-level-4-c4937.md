---
title: Upozornění (úroveň 4) C4937 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4937
dev_langs:
- C++
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7bc6232458b357f41e859c58d4b6b77f78ef2a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118294"
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