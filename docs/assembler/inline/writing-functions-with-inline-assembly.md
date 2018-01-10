---
title: "Zápis funkcí s vloženým sestavením | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2fc9e6a1d2c94e74ef8aabf085af8fc4dc0bc28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="writing-functions-with-inline-assembly"></a>Zápis funkcí s vloženým sestavením
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Pokud píšete funkce s kódu vnořeného sestavení, je snadné předání argumentů funkce a vrácení hodnoty z něj. Následující příklady porovnat funkce nejprve napsané pro samostatné assembleru a pak přepsaná pro vložený assembler. Volaná funkce `power2`, obdrží dva parametry, první parametr vynásobí 2 exponentem druhý parametr. Napsané pro samostatné assembleru, funkce může vypadat například takto:  
  
```  
; POWER.ASM  
; Compute the power of an integer  
;  
       PUBLIC _power2  
_TEXT SEGMENT WORD PUBLIC 'CODE'  
_power2 PROC  
  
        push ebp        ; Save EBP  
        mov ebp, esp    ; Move ESP into EBP so we can refer  
                        ;   to arguments on the stack  
        mov eax, [ebp+4] ; Get first argument  
        mov ecx, [ebp+6] ; Get second argument  
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )  
        pop ebp         ; Restore EBP  
        ret             ; Return with sum in EAX  
  
_power2 ENDP  
_TEXT   ENDS  
        END  
```  
  
 Vzhledem k tomu, že je napsán pro samostatné assembleru, vyžaduje funkci samostatného zdrojového souboru a sestavení a odkaz kroky. C a C++ argumenty funkce se obvykle předávají v zásobníku, takže tato verze `power2` funkce přistupuje k její argumenty podle jejich umístění v zásobníku. (Všimněte si, že **modelu** – direktiva, k dispozici v MASM a některé další kompletující, taky umožňuje přístup k argumenty zásobníku a místní zásobníku proměnné podle názvu.)  
  
## <a name="example"></a>Příklad  
 Zapíše tento program `power2` funkce s kódu vnořeného sestavení:  
  
```  
// Power2_inline_asm.c  
// compile with: /EHsc  
// processor: x86  
  
#include <stdio.h>  
  
int power2( int num, int power );  
  
int main( void )  
{  
    printf_s( "3 times 2 to the power of 5 is %d\n", \  
              power2( 3, 5) );  
}  
int power2( int num, int power )  
{  
   __asm  
   {  
      mov eax, num    ; Get first argument  
      mov ecx, power  ; Get second argument  
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )  
   }  
   // Return with result in EAX  
}  
```  
  
 Vložené verzi `power2` funkce odkazuje na její argumenty podle názvu a zobrazí se ve stejném souboru zdroj jako zbytek programu. Tato verze taky vyžaduje méně pokyny sestavení.  
  
 Protože verze vložené `power2` neprovede a C `return` příkaz způsobí neškodné upozornění Pokud zkompilujete na úrovni upozornění 2 nebo vyšší. Funkce vrátí hodnotu, ale kompilátor nelze zjistit, který neexistuje `return` příkaz. Můžete použít [#pragma – upozornění](../../preprocessor/warning.md) zakázat generování toto upozornění.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)