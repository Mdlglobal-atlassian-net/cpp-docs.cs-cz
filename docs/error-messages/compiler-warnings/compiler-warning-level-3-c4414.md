---
title: Kompilátor upozornění (úroveň 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 0a9ceb332888e306b8cb3bcbe1832f773d02d63d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629811"
---
# <a name="compiler-warning-level-3-c4414"></a>Kompilátor upozornění (úroveň 3) C4414

'function': skok short na funkci se převedl na near

Krátký přeskakování generovat compact instrukce, což větve adresa v rámci omezený rozsah z podle pokynů. Instrukce zahrnuje krátký posun, která představuje vzdálenost mezi odkaz a cílová adresa definici funkce. Během propojování funkce může být přesunutý nebo mohou podléhat propojování optimalizace, které způsobují funkci přesunout mimo rozsah dosažitelný z krátký posun. Kompilátor musí generovat speciální záznam pro odkaz, který vyžaduje skok (jmp) instrukce BLÍZKÉ nebo úplně. Kompilátor provést převod.

Například následující kód vygeneruje C4414:

```
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```