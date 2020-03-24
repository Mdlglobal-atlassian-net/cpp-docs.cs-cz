---
title: Volání funkcí jazyka C v sestavení inline assemblerem
ms.date: 08/30/2018
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
ms.openlocfilehash: 94bbfda3a5fd15885f3d8276d506541418a9489f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169588"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Volání funkcí jazyka C v sestavení inline assemblerem

**Specifické pro společnost Microsoft**

Blok `__asm` může volat funkce jazyka C, včetně rutin knihovny jazyka C. Následující příklad volá rutinu knihovny `printf`:

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

Vzhledem k tomu, že argumenty funkce jsou předány v zásobníku, stačí před voláním funkce jednoduše vložit potřebné argumenty – ukazatelé řetězce v předchozím příkladu –. Argumenty jsou vloženy v obráceném pořadí, takže se z zásobníku přidávají v požadovaném pořadí. Emulace příkazu jazyka C

```cpp
printf( format, hello, world );
```

příklad vloží ukazatele na `world`, `hello`a `format`v tomto pořadí a potom zavolá `printf`.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
