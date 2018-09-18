---
title: Chyba kompilátoru C3056 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3056
dev_langs:
- C++
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0495bc9c31df3aa3ff47ef860e8e47ea6f7c2248
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063577"
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