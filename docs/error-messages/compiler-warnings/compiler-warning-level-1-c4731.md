---
title: Upozornění kompilátoru (úroveň 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: 72483b734a1463b7b211c49ef21a01536ffa0ea1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185721"
---
# <a name="compiler-warning-level-1-c4731"></a>Upozornění kompilátoru (úroveň 1) C4731

' pointer ': registr ukazatele rámce ' register ' změněn pomocí vloženého kódu sestavení

Registr ukazatele na rámec byl změněn. Je nutné uložit a obnovit registr ve vloženém bloku sestavení nebo proměnné rámce (místní nebo parametr, v závislosti na změně registru), nebo váš kód nemusí fungovat správně.

Následující ukázka generuje C4731:

```cpp
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

EBP je ukazatel na rámec (! není povolen) a je upravován. Pokud na `p` později odkazuje, je odkazováno vzhledem k `EBP`. `EBP` však byl kód přepsán, takže program nebude správně fungovat a může dokonce dojít k chybě.
