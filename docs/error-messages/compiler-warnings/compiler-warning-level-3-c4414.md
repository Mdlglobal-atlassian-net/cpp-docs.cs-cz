---
title: Upozornění (úroveň 3) C4414 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd0868fea89cd868178956c0aba171ce6525bd75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043206"
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