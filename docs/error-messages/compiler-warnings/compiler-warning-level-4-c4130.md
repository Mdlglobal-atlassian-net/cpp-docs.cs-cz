---
title: Upozornění (úroveň 4) C4130 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4130
dev_langs:
- C++
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21d73595e41c4c83eda61fa749c9f2dc72bb14bc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038097"
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