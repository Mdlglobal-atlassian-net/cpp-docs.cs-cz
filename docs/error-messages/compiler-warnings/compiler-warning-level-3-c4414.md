---
title: Upozornění kompilátoru (úroveň 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 4625f6bdb4aa6fe86ca881a8e36e5673e55ccb87
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185591"
---
# <a name="compiler-warning-level-3-c4414"></a>Upozornění kompilátoru (úroveň 3) C4414

' function ': krátký skok na funkci převedený na Near

Krátké odkazy generují kompaktní instrukce, které větví na adresu v omezeném rozsahu od instrukce. Instrukce obsahuje krátký posun, který představuje vzdálenost mezi skokem a cílovou adresou, definicí funkce. Během propojení funkce může dojít k přesunu nebo předmětu optimalizace v době propojení, která způsobí, že funkce bude přesunuta mimo rozsah dosažitelný z krátkého posunu. Kompilátor musí vygenerovat speciální záznam pro skok, který vyžaduje, aby instrukce skok byla buď blízko, nebo daleko. Kompilátor provedl převod.

Například následující kód generuje C4414:

```cpp
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
