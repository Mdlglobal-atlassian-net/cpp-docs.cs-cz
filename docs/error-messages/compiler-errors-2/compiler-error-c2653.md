---
title: Chyba kompilátoru C2653
ms.date: 11/30/2017
f1_keywords:
- C2653
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
ms.openlocfilehash: d4a3a8a74483317b87e16458f44016f0aeca1379
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350777"
---
# <a name="compiler-error-c2653"></a>Chyba kompilátoru C2653

> "*identifikátor*': není název třídy nebo oboru názvů

Syntaxe jazyka vyžaduje třídy, struktury, sjednocení nebo název oboru názvů.

Této chybě může dojít, pokud použijete název, který nebyl deklarován jako třídy, struktury, sjednocení nebo obor názvů před operátor rozsahu. Chcete-li vyřešit tento problém, deklarovat název nebo zahrnout záhlaví, který deklaruje název, než bude použit.

C2653 je také možné, pokud se pokusíte k definování *složené obor názvů*, obor názvů, který obsahuje jeden nebo více názvů vnořené oboru názvů. Složené obor názvů, který definice nejsou povoleny v jazyce C++ před C ++ 17. Složené obory názvů jsou podporované od verze Visual Studio 2015 Update 3 při zadávání [/std: c ++ nejnovější](../../build/reference/std-specify-language-standard-version.md) – možnost kompilátoru. Počínaje verzí Visual C++ 2017 verze 15.5, kompilátor podporuje definice oboru názvů složené při [/std: c ++ 17](../../build/reference/std-specify-language-standard-version.md) je zadána možnost.

## <a name="examples"></a>Příklady

Tato ukázka vygeneruje C2653, protože název oboru se používá, ale není deklarovaná. Kompilátor očekává, že třídy, struktury, sjednocení nebo název oboru názvů před operátoru oboru (::).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

V kódu, který není zkompilován pro C ++ 17 a novějších standardy musí vnořené obory názvů pomocí deklarace oboru názvů explicitní na každou úroveň vnoření:

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
