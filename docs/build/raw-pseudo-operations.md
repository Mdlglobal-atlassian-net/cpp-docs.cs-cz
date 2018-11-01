---
title: Pseudooperace s nezpracovanými daty
ms.date: 11/04/2016
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
ms.openlocfilehash: 04dfe4d59c05dfcf22d0e64063fbc4953cbcb2f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538024"
---
# <a name="raw-pseudo-operations"></a>Pseudooperace s nezpracovanými daty

Toto téma obsahuje seznam pseudo operace.

## <a name="remarks"></a>Poznámky

|Operace pseudostavů.|Popis|
|----------------------|-----------------|
|PROC rámce [: ehandler]|Způsobí, že MASM generovat funkci položka v .pdata tabulky a vrátit se zpět informace v .xdata funkce uživatele strukturované zpracování výjimek unwind chování.  Pokud ehandler je k dispozici, tento proces je zadána v .xdata jako obslužná rutina pro konkrétní jazyk.<br /><br /> Při použití atributu rámce, musí být následován znakem. ENDPROLOG směrnice.  Pokud je funkce – funkce typu list (jak je definováno v [typy funkcí](../build/function-types.md)) atribut rámce je zbytečné, jako jsou zbývající část těchto pseudo operací.|
|. PUSHREG registru|Vytvoří položku UWOP_PUSH_NONVOL unwind kódu pro zadaný registr číslo pomocí aktuální posun v prologu.<br /><br /> To by měla sloužit pouze s registry stálé celé číslo.  Nabízená oznámení volatile registrů, použijte. ALLOCSTACK 8 místo|
|. Posun SETFRAME registru|Výplně v rámci registrace pole a posun v informacích o unwind pomocí zadaného registru a posun. Posun musí být násobkem 16 a menší než nebo rovna 240. Tato direktiva generuje také položku UWOP_SET_FPREG unwind kódu pro zadaný registr pomocí aktuální posun prologu.|
|. Velikost ALLOCSTACK|Generuje UWOP_ALLOC_SMALL nebo UWOP_ALLOC_LARGE se zadanou velikostí pro aktuální posun v prologu.<br /><br /> Velikost operand musí být násobkem 8.|
|. Posun SAVEREG registru|Generuje UWOP_SAVE_NONVOL nebo položku UWOP_SAVE_NONVOL_FAR unwind kódu pro zadaný registr a posun pomocí aktuální posun prologu. MASM zvolí nejúčinnější kódování.<br /><br /> Posun musí být kladná a násobkem 8.  Posun je relativní vzhledem k základní třídě rámce podle postupu, který je obvykle ve RSP, nebo pokud používáte rámcový ukazatel ukazatel na rámec bez měřítka.|
|. Posun SAVEXMM128 registru|Generuje UWOP_SAVE_XMM128 nebo položku UWOP_SAVE_XMM128_FAR unwind kódu pro zadaný Registr XMM a posun pomocí aktuální posun prologu. MASM zvolí nejúčinnější kódování.<br /><br /> Posun musí být kladná a násobkem 16.  Posun je relativní vzhledem k základní třídě rámce podle postupu, který je obvykle ve RSP, nebo pokud používáte rámcový ukazatel ukazatel na rámec bez měřítka.|
|. PUSHFRAME [kód]|Vytvoří položku UWOP_PUSH_MACHFRAME unwind kódu. Pokud je zadán nepovinný kód, dostane položku unwind kódu Modifikátor 1. V opačném případě Modifikátor je 0.|
|.ENDPROLOG|Signalizuje konec deklarace prologu.  Musí proběhnout v první 255 bajtů funkce.|

Tady je ukázkový prolog funkce s správné použití většiny operační kódy:

```
sample PROC FRAME
   db      048h; emit a REX prefix, to enable hot-patching
push rbp
.pushreg rbp
sub rsp, 040h
.allocstack 040h
lea rbp, [rsp+020h]
.setframe rbp, 020h
movdqa [rbp], xmm7
.savexmm128 xmm7, 020h;the offset is from the base of the frame
;not the scaled offset of the frame
mov [rbp+018h], rsi
.savereg rsi, 038h
mov [rsp+010h], rdi
.savereg rdi, 010h; you can still use RSP as the base of the frame
; or any other register you choose
.endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

sub rsp, 060h

; we can unwind from the following AV because of the frame pointer

mov rax, 0
mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

movdqa xmm7, [rbp]
mov rsi, [rbp+018h]
mov rdi, [rbp-010h]

; Here’s the official epilog

lea rsp, [rbp-020h]
pop rbp
ret
sample ENDP
```

## <a name="see-also"></a>Viz také

[Unwind pomocníci pro MASM](../build/unwind-helpers-for-masm.md)