---
title: Zápis funkcí s vloženým sestavením
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
ms.openlocfilehash: 7848a8f071f50f8d809a999a96a9c0f8193c480e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166851"
---
# <a name="writing-functions-with-inline-assembly"></a>Zápis funkcí s vloženým sestavením

**Microsoft Specific**

Při zápisu funkce s vložený kód sestavení, je snadné předávat argumenty funkci a vrátí hodnotu z něj. Následující příklady porovnávají funkce nejprve napsané pro službu používat samostatný kompilátor, poté přepsána pro vložený assembler. Volaná funkce `power2`, přijímá dva parametry, vynásobení prvního parametru 2 k elektrické energie druhý parametr. Napsané pro používat samostatný kompilátor, funkce může vypadat takto:

```asm
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

Protože je určené pro používat samostatný kompilátor, vyžaduje funkci samostatného zdrojového souboru a sestavení a propojení kroky. Argumenty funkce jazyka C a C++ jsou obvykle předány v zásobníku, takže tato verze `power2` funkce přistupuje k jeho argumentů podle pozice v zásobníku. (Všimněte si, že **modelu** směrnice, které jsou k dispozici v MASM a některé další montážního podniku, taky umožňuje přístup k místní zásobník proměnné a argumenty zásobníku podle názvu.)

## <a name="example"></a>Příklad

Tento program zapíše `power2` funkce pomocí vloženého kódu sestavení:

```cpp
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

Vložené verzi `power2` funkce odkazuje argumenty podle názvu a zobrazí se ve stejném zdrojovém souboru jako zbytek programu. Tato verze také vyžaduje méně pokyny k sestavení.

Protože verze vložené `power2` neprovede C `return` příkazu, to způsobí, že se neškodné upozornění Pokud kompilujete na úroveň upozornění 2 nebo vyšší. Funkce vrátí hodnotu, ale kompilátor nemůže určit, které chybí `return` příkazu. Můžete použít [varování #pragma](../../preprocessor/warning.md) zakázat generování toto upozornění.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>