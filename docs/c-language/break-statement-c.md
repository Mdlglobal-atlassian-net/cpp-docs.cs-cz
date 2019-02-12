---
title: break – příkaz (C)
ms.date: 11/04/2016
f1_keywords:
- break
helpviewer_keywords:
- break keyword [C]
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
ms.openlocfilehash: b38ff6c535c142bd15ea09a4d7c80010c3fff31f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149814"
---
# <a name="break-statement-c"></a>break – příkaz (C)

Příkaz `break` ukončí spouštění nejbližšího nadřazeného příkazu `do`, `for`, `switch` nebo `while`, v němž se vyskytuje. Řízení je předáno příkazu, který následuje ukončený příkaz.

## <a name="syntax"></a>Syntaxe

*příkaz-skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Konec;**

Příkaz `break` se často používá k ukončení zpracování konkrétního případu v příkazu `switch`. Absence nadřazeného iterativního příkazu nebo příkazu `switch` způsobí chybu.

V rámci vnořených příkazů příkaz `break` ukončí pouze příkaz `do`, `for`, `switch` nebo `while`, který jej bezprostředně obklopuje. Pomocí příkazu `return` nebo `goto` lze převést řízení jinam mimo vnořenou strukturu.

Následující příklad znázorňuje příkaz `break`:

```
#include <stdio.h>
int main() {
   char c;
   for(;;) {
      printf_s( "\nPress any key, Q to quit: " );

      // Convert to character value
      scanf_s("%c", &c);
      if (c == 'Q')
          break;
   }
} // Loop exits only when 'Q' is pressed
```

## <a name="see-also"></a>Viz také:

[break – příkaz](../cpp/break-statement-cpp.md)
