---
title: Chyba kompilátoru C3005
ms.date: 11/04/2016
f1_keywords:
- C3005
helpviewer_keywords:
- C3005
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
ms.openlocfilehash: 1303fd667c92af6fd8d0476da9468b4c7d090e6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444301"
---
# <a name="compiler-error-c3005"></a>Chyba kompilátoru C3005

"error_text": "direktiva" direktivy OpenMP se našel neočekávaný token

Direktivě OpenMP byl chybně vytvořen.

Následující ukázka generuje C3005:

```
// C3005.c
// compile with: /openmp
int main()
{
   #pragma omp parallel + for   // C3005
}
```

C3005 může také dojít, pokud je umístit levou složenou závorku na stejném řádku jako direktivy pragma.

```
// C3005b.c
// compile with: /openmp
int main() {
   #pragma omp parallel {   // C3005 put open brace on next line
   lbl2:;
   }
   goto lbl2;
}
```