---
title: Chyba kompilátoru C3012 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3012
dev_langs:
- C++
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99bdac5ffb75978479ae7ef420a48b3d1b2f8e64
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063668"
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