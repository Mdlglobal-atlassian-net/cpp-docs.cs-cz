---
title: Chyba kompilátoru C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: 972ec6591132443ef4d1297598d6de7216f59663
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586690"
---
# <a name="compiler-error-c2429"></a>Chyba kompilátoru C2429

> "*funkci jazyka*"vyžaduje příznak kompilátoru"*– možnost kompilátoru*.

Funkce jazyka vyžaduje parametr kompilátoru specifické pro podporu.

Chyba **C2429: jazyk funkce "vnořené oboru názvů definice" vyžaduje příznak kompilátoru "/ std: c ++ 17.** je generována, pokud se pokusíte k definování *složené obor názvů*, obor názvů, který obsahuje jeden nebo více názvy vnořené oboru oborů názvů, počínaje verzí Visual Studio 2015 Update 5. (V sadě Visual Studio 2017 verze 15.3, **/std: c ++ nejnovější** je vyžadován přepínač.) Složené obor názvů, který definice nejsou povoleny v jazyce C++ před C ++ 17. Kompilátor podporuje definice oboru názvů složené při [/std: c ++ 17](../../build/reference/std-specify-language-standard-version.md) je zadána možnost kompilátoru:

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
