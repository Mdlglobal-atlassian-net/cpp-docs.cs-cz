---
title: Chyba kompilátoru C3005
ms.date: 11/04/2016
f1_keywords:
- C3005
helpviewer_keywords:
- C3005
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
ms.openlocfilehash: b260879dfafbe40ab13d14f7208f1ffbc90b9826
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302156"
---
# <a name="compiler-error-c3005"></a>Chyba kompilátoru C3005

' error_text ': v direktivě OpenMP direktivy se zjistil neočekávaný token.

Direktiva OpenMP byla nesprávně vytvořena.

Následující ukázka generuje C3005:

```c
// C3005.c
// compile with: /openmp
int main()
{
   #pragma omp parallel + for   // C3005
}
```

K C3005 může také dojít, pokud vložíte levou složenou závorku na stejný řádek jako direktivu pragma.

```c
// C3005b.c
// compile with: /openmp
int main() {
   #pragma omp parallel {   // C3005 put open brace on next line
   lbl2:;
   }
   goto lbl2;
}
```
