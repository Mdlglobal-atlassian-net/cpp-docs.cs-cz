---
title: Chyba kompilátoru C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: 022bc1a37f7d9cfdb2c206592dd303a9c3c95080
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749110"
---
# <a name="compiler-error-c3899"></a>Chyba kompilátoru C3899

var: použití l-value datového členu initonly není povolené přímo v rámci paralelní oblasti třídy Class.

Datový člen [initonlyC++(/CLI)](../../dotnet/initonly-cpp-cli.md) nejde inicializovat uvnitř této části konstruktoru, který je v [paralelní](../../parallel/openmp/reference/parallel.md) oblasti.  Důvodem je, že kompilátor provede interní přemístění tohoto kódu, což znamená, že již není součástí konstruktoru.

Chcete-li vyřešit, inicializujte datový člen initonly v konstruktoru, ale mimo paralelní oblast.

## <a name="example"></a>Příklad

Následující ukázka generuje C3899.

```cpp
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```
