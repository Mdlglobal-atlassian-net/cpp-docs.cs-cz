---
title: Upozornění kompilátoru (úrovně 3 a 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: a12bee4591df8a7a952dc741c4b26c637bb5256c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991072"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Upozornění kompilátoru (úrovně 3 a 4) C4244

konverze Conversion z ' typ1 ' na ' typ2 ', může dojít ke ztrátě dat

Celočíselný typ je převeden na menší celočíselný typ. Toto je upozornění úrovně 4, pokud je *typ1* `int` a *typ2* je menší než `int`. V opačném případě je to úroveň 3 (přiřazena hodnota typu [__int64](../../cpp/int8-int16-int32-int64.md) proměnné typu `unsigned int`). Možná došlo ke ztrátě dat.

Pokud získáte C4244, měli byste buď změnit program na používání kompatibilních typů, nebo přidat do kódu určitou logiku, abyste zajistili, že rozsah možných hodnot bude vždy kompatibilní s typy, které používáte.

C4244 může také být v úrovni 2 požáru. Další informace najdete v tématu [Upozornění kompilátoru (úroveň 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) .

Převod může mít problém z důvodu implicitních převodů.

Následující ukázka generuje C4244:

```cpp
// C4244_level4.cpp
// compile with: /W4
int aa;
unsigned short bb;
int main() {
   int b = 0, c = 0;
   short a = b + c;   // C4244

   bb += c;   // C4244
   bb = bb + c;   // C4244
   bb += (unsigned short)aa;   // C4244
   bb = bb + (unsigned short)aa;   // OK
}
```

Další informace najdete v tématu [obvyklé aritmetické převody](../../c-language/usual-arithmetic-conversions.md).

```cpp
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

Při vytváření kódu pro 64 cíle, které negenerují upozornění při sestavování pro 32 bitové cíle, může dojít k C4244 upozornění. Například rozdíl mezi ukazateli je 32 množství na 32ch platformách, 64 ale množství na 64-bitové platformě.

Následující ukázka generuje C4244 při kompilování pro 64 cíle:

```cpp
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```
