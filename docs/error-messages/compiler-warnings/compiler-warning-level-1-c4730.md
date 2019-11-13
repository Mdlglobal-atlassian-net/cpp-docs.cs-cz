---
title: Upozornění kompilátoru (úroveň 1) C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: 5cdd6018afd26b09f7a4555ff8d0431c3364f09e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051328"
---
# <a name="compiler-warning-level-1-c4730"></a>Upozornění kompilátoru (úroveň 1) C4730

' Main ': kombinování _m64 a výrazů s plovoucí desetinnou čárkou může mít za následek nesprávný kód

Funkce používá [__m64](../../cpp/m64.md) a **float**/**dvojitých** typů. Vzhledem k tomu, že registry MMX a plovoucí desetinné čárky sdílejí stejný fyzický prostor registru (nelze použít současně), pomocí `__m64` a **float**/**dvojitých** typů ve stejné funkci může dojít k poškození dat, což může způsobit výjimku.

Aby bylo možné bezpečně používat typy `__m64` a typy s plovoucí desetinnou čárkou ve stejné funkci, každá instrukce, která používá jeden z typů, by měla být oddělena **_m_empty ()** (pro MMX) nebo **_m_femms ()** (pro 3DNow!).

Následující ukázka generuje C4730:

```cpp
// C4730.cpp
// compile with: /W1
// processor: x86
#include "mmintrin.h"

void func(double)
{
}

int main(__m64 a, __m64 b)
{
   __m64 m;
   double f;
   f = 1.0;
   m = _m_paddb(a, b);
   // uncomment the next line to resolve C4730
   // _m_empty();
   func(f * 3.0);   // C4730
}
```