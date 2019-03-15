---
title: Upozornění kompilátoru (úrovně 3 a 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: af06dbf5bb4a1dd133c277d63c40da2a8a54770b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822246"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Upozornění kompilátoru (úrovně 3 a 4) C4244

"conversion" převod z 'type1' na 'type2', možná ztráta dat

Celočíselný typ je převedena na menší typ celé číslo. Toto je upozornění úrovně 4 Pokud *type1* je `int` a *type2* je menší než `int`. V opačném případě je úroveň 3 (přiřazena hodnota typu [__int64](../../cpp/int8-int16-int32-int64.md) na proměnnou typu `unsigned int`). Může dojít ke ztrátě dat, mohlo dojít.

Pokud se zobrazí C4244, si změnit program používat typy kompatibilní, nebo přidat nějaké logiky do kódu, aby se zajistilo, že rozsah možných hodnot bude vždy kompatibilní s typy, které používáte.

Na úrovni 2; můžete také vyvolat C4244 Zobrazit [upozornění kompilátoru (úroveň 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) Další informace.

Převod může být problém z důvodu implicitní převody.

Následující ukázka generuje C4244:

```
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

```
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

Upozornění C4244 může dojít při sestavování kódu pro 64bitové cíle, který negeneruje upozornění, při sestavování pro 32-bit cíle. Rozdíl mezi ukazatele je například množství 32-bit na 32bitových platformách, ale množství 64-bit na 64bitových platformách.

Následující ukázka generuje C4244 při kompilaci pro 64bitové cíle:

```
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```