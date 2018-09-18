---
title: Chyba kompilátoru C3899 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3899
dev_langs:
- C++
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b154941051e1c6887e8e05756befd6a18c62ed72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091777"
---
# <a name="compiler-error-c3899"></a>Chyba kompilátoru C3899

'příkaz var': použití l-value datového členu initonly není povolené přímo v rámci paralelní oblastí v třídě 'class'

[Initonly (C + +/ CLI)](../../dotnet/initonly-cpp-cli.md) uvnitř konstruktor, který je v této části se nedá inicializovat datový člen [paralelní](../../parallel/openmp/reference/parallel.md) oblasti.  Je to proto kompilátor udělá interní přemístění tento kód tak, že už efektivně nejsou součástí konstruktoru.

Pokud chcete vyřešit, inicializujte datového členu initonly v konstruktoru, ale mimo paralelní oblasti.

## <a name="example"></a>Příklad

Následující ukázka generuje C3899.

```
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