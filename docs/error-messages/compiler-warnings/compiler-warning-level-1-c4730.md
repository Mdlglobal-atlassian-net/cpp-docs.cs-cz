---
title: Upozornění kompilátoru (úroveň 1) C4730
ms.date: 11/04/2016
f1_keywords:
- C4730
helpviewer_keywords:
- C4730
ms.assetid: 11303e3f-162b-4b19-970a-479686123a68
ms.openlocfilehash: 4da60194deaeac3c79f8c3e9be3bd87d91bc7ca2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487032"
---
# <a name="compiler-warning-level-1-c4730"></a>Upozornění kompilátoru (úroveň 1) C4730

"hlavní": směšování výrazů _m64 a plovoucí desetinná čárka výrazy mohou způsobit nesprávný kód

Funkce používá [__m64](../../cpp/m64.md) a **float**/**double** typy. Protože MMX a s plovoucí desetinnou čárkou registrů sdílet stejný fyzický prostor registru (nelze použít současně), pomocí `__m64` a **float**/**double** typů ve stejném funkce může způsobit poškození dat, což může způsobit výjimku.

Bezpečně používat `__m64` typy a typy s plovoucí desetinnou čárkou ve stejné funkci každou instrukci, která používá jeden z typů musí být odděleny **_m_empty()** (pro MMX) nebo **_m_femms()** (pro 3DNow!) vnitřní.

Následující ukázka generuje C4730:

```
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