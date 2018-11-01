---
title: Kompilátor upozornění (úroveň 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: 1b1fb72d68309a4bef56ccd844ad30d967bbadbd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552942"
---
# <a name="compiler-warning-level-4-c4130"></a>Kompilátor upozornění (úroveň 4) C4130

'operator': logická operace s adresou konstanty typu string

Použití operátoru s adresou řetězcového literálu vytvoří neočekávaný kód.

Následující ukázka generuje C4130:

```
// C4130.cpp
// compile with: /W4
int main()
{
   char *pc;
   pc = "Hello";
   if (pc == "Hello") // C4130
   {
   }
}
```

**Pokud** příkaz porovnává hodnotu uloženou v ukazateli `pc` adresu řetězec "Hello", který je přidělen samostatně pokaždé, když dojde k řetězec v kódu. **Pokud** příkazu není výsledkem porovnání řetězce, na které odkazuje `pc` pomocí řetězce "Hello".

Chcete-li porovnat řetězce, použijte `strcmp` funkce.