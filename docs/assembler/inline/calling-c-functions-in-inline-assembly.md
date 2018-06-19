---
title: Funkce volání C ve vloženém sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: c3f6d03ba77c7a4cdb3478a1bfe8729019dea002
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049515"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Volání funkcí jazyka C v sestavení inline assemblerem
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 `__asm` Bloku můžete volání funkcí jazyka C, včetně rutiny C knihovny. Následující příklad volání `printf` rutiny knihovny:  
  
```  
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
  
 Protože jsou argumenty funkce předány v zásobníku, jednoduše push potřebné argumenty – řetězec ukazatele v předchozím příkladu – před voláním funkce. Argumenty, které se instaluje v obráceném pořadí, které pocházejí ze zásobníku v požadované pořadí. Emulovat příkaz jazyka C  
  
```  
printf( format, hello, world );  
```  
  
 v příkladu nabízených oznámení ukazatele na `world`, `hello`, a `format`, v pořadí a pak volání `printf`.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vkládaný assembler](../../assembler/inline/inline-assembler.md)