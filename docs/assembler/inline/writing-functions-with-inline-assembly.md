---
title: Zápis funkcí s vloženým sestavením
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], inline assembly
- inline assembly [C++], writing functions
- assembler [C++], writing functions
- __asm keyword [C++], in functions
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
ms.openlocfilehash: 5416a29477651c496d83e6ee215a2cb88ba26e3b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169055"
---
# <a name="writing-functions-with-inline-assembly"></a>Zápis funkcí s vloženým sestavením

**Specifické pro společnost Microsoft**

Pokud napíšete funkci s vloženým kódem sestavení, je snadné předat argumenty funkce a vrátit hodnotu z ní. V následujících příkladech se porovnávají funkce napsané pro samostatný assembler a pak se přepsaly pro Inline assembler. Funkce s názvem `power2`přijímá dva parametry a vynásobení prvního parametru 2 k mocnině druhého parametru. Napsáno pro samostatný Assembler, funkce může vypadat takto:

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

Vzhledem k tomu, že je zapsána pro samostatný Assembler, funkce vyžaduje samostatný zdrojový soubor a kroky sestavení a propojení. Argumenty jazyka C++ C a jsou obvykle předány do zásobníku, takže tato verze funkce `power2` přistupuje k argumentům jejich pozicemi v zásobníku. (Všimněte si, že direktiva **model** , která je dostupná v MASM a některé jiné assemblery, vám také umožní přistupovat k argumentům zásobníku a k místním proměnným zásobníku podle názvu.)

## <a name="example"></a>Příklad

Tento program zapisuje funkci `power2` s vloženým kódem sestavení:

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

Vložená verze funkce `power2` odkazuje na její argumenty podle názvu a zobrazí se ve stejném zdrojovém souboru jako zbytek programu. Tato verze také vyžaduje méně instrukcí sestavení.

Vzhledem k tomu, že vložená verze `power2` neprovede příkaz jazyka C `return`, způsobuje při kompilaci na úrovni upozornění 2 nebo vyšší neškodné upozornění. Funkce vrací hodnotu, ale kompilátor nemůže sdělit, že v případě absence příkazu `return`. Pokud chcete zakázat generování tohoto upozornění, můžete použít [upozornění #pragma](../../preprocessor/warning.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
