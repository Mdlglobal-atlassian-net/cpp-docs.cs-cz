---
title: Chyba kompilátoru C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 9fe0ac7d3637cad3a5571c4631345dac1a0021bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503081"
---
# <a name="compiler-error-c3012"></a>Chyba kompilátoru C3012

> "*vnitřní*': vnitřní funkce není povolená přímo v paralelní oblasti

A [vnitřní kompilátor](../../intrinsics/compiler-intrinsics.md) funkce není povolena v `omp parallel` oblasti. Chcete-li vyřešit tento problém, přesunout vnitřních objektů mimo oblast nebo nahradíte je ekvivalenty – vnitřní.

## <a name="example"></a>Příklad

Následující ukázka generuje C3012 a ukazuje jeden způsob, jak ho opravit:

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```