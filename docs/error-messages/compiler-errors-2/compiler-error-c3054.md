---
title: Chyba kompilátoru C3054
ms.date: 11/04/2016
f1_keywords:
- C3054
helpviewer_keywords:
- C3054
ms.assetid: 6f4b7ac5-0d12-474b-b611-76ff26ee41ac
ms.openlocfilehash: 1dd6450d661700d9b2f7f94e625abd9ecc64ed08
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772992"
---
# <a name="compiler-error-c3054"></a>Chyba kompilátoru C3054

v obecné třídě nebo funkci aktuálně nepodporuje "#pragma omp parallel.

Další informace najdete v tématu [obecných typů](../../extensions/generics-cpp-component-extensions.md) a [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3054.

```
// C3054.cpp
// compile with: /openmp /clr /c
#include <omp.h>

ref struct MyBaseClass {
   // Delete the following 7 lines to resolve.
   generic <class ItemType>
   void Test(ItemType i) {   // C3054
      #pragma omp parallel num_threads(4)
      {
         int i = omp_get_thread_num();
      }
   }

   // OK
   void Test2() {
      #pragma omp parallel num_threads(4)
      {
         int i = omp_get_thread_num();
      }
   }
};
```