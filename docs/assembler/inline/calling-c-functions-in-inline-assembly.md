---
title: Funkce volání jazyka C ve vloženém sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a080c05aee58a2e6ffae17d14e99c66922aa1f17
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686684"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Volání funkcí jazyka C v sestavení inline assemblerem

**Specifické pro Microsoft**

`__asm` Bloku může volat funkce jazyka C, včetně rutiny knihoven C. Následující příklad volá `printf` rutina knihovny:

```cpp
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp
// processor: x86
#include <stdio.h>

char format[] = "%s %s\n";
char hello[] = "Hello";
char world[] = "world";
int main( void )
{
   __asm
   {
      mov  eax, offset world
      push eax
      mov  eax, offset hello
      push eax
      mov  eax, offset format
      push eax
      call printf
      //clean up the stack so that main can exit cleanly
      //use the unused register ebx to do the cleanup
      pop  ebx
      pop  ebx
      pop  ebx
   }
}
```

Protože jsou argumenty funkce předány v zásobníku, stačí vložit potřebné argumenty – řetězec ukazatele v předchozím příkladu – před voláním funkce. Argumenty jsou posunuty v obráceném pořadí, které pocházejí ze zásobníku do požadovaného pořadí. Pro emulaci příkazů jazyka C

```cpp
printf( format, hello, world );
```

v příkladu nabízených oznámení ukazatele na `world`, `hello`, a `format`, v tomto pořadí a poté zavolá `printf`.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>