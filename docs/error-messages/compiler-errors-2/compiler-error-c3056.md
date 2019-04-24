---
title: Chyba kompilátoru C3056
ms.date: 11/04/2016
f1_keywords:
- C3056
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
ms.openlocfilehash: d33aa6679c6dc68b7f1a62e75aff6fadc65dc7bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265604"
---
# <a name="compiler-error-c3056"></a>Chyba kompilátoru C3056

'symbol': symbol není ve stejném oboru jako direktiva threadprivate.

Symbol použitý v [threadprivate](../../parallel/openmp/reference/threadprivate.md) klauzule musí být ve stejném oboru jako `threadprivate` klauzuli.

Následující ukázka generuje C3056:

```
// C3056.cpp
// compile with: /openmp
int x, y;
void test() {
   #pragma omp threadprivate(x, y)   // C3056
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Možná řešení:

```
// C3056b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)
void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```