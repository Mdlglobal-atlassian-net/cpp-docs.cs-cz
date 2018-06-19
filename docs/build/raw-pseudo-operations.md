---
title: Pseudooperace s nezpracovanými | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4def1a0e-ec28-4736-91fb-fac95fba1f36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff3b9dd065b4bf1f64950f97237dec08b10d23cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369926"
---
# <a name="raw-pseudo-operations"></a>Pseudooperace s nezpracovanými daty
Toto téma uvádí pseudo operace.  
  
## <a name="remarks"></a>Poznámky  
  
|Operace pseudo|Popis|  
|----------------------|-----------------|  
|PROC rámce [: ehandler]|Příčiny MASM ke generování funkci tabulky položku v .pdata a unwind informace v .xdata pro funkci je strukturovaná výjimek unwind chování.  Pokud se nachází ehandler, tato procedura je zadána v .xdata jako obslužná rutina pro konkrétní jazyk.<br /><br /> Pokud je použit atribut RÁMEČKU, musí být sledována. Direktiva ENDPROLOG.  Pokud funkce je funkce, typu list (podle definice v [typy funkce](../build/function-types.md)) je zbytečné, jako jsou zbytek tyto pseudo operace atribut rámce.|  
|. PUSHREG registru|Generuje položku UWOP_PUSH_NONVOL unwind kód pro číslo zadané registrace používá aktuální posun v prologu.<br /><br /> Mělo by být použito pouze s registry stálé celé číslo.  Posuny volatile registrů, použijte. ALLOCSTACK 8, místo toho|  
|. Posun SETFRAME registru|Vyplní rámečku registraci pole a posun v unwind informace, pomocí zadané registrace a posun. Posun musí být násobkem 16 a menší než nebo rovna 240. Tato direktiva také generuje položku UWOP_SET_FPREG unwind kód pro zadané zaregistrovat pomocí aktuální posun prologu.|  
|. Velikost ALLOCSTACK|Generuje UWOP_ALLOC_SMALL nebo UWOP_ALLOC_LARGE se zadanou velikostí pro aktuální posun v prologu.<br /><br /> Operand velikost musí být násobkem 8.|  
|. Posun SAVEREG registru|Generuje UWOP_SAVE_NONVOL nebo položku UWOP_SAVE_NONVOL_FAR unwind kód pro zadané registrace a použití aktuální posun prologu posun. MASM vybere nejúčinnější kódování.<br /><br /> Posun musí být kladná a násobkem 8.  Posun je relativní vzhledem k základní rámce postupu, který je obvykle v konfigurace, nebo, pokud se používá ukazatel na rámec, bez měřítka rámec ukazatele.|  
|. Posun SAVEXMM128 registru|Generuje UWOP_SAVE_XMM128 nebo položku UWOP_SAVE_XMM128_FAR unwind kód pro zadané XMM registrace a použití aktuální posun prologu posun. MASM vybere nejúčinnější kódování.<br /><br /> Posun musí být kladná a násobkem 16.  Posun je relativní vzhledem k základní rámce postupu, který je obvykle v konfigurace, nebo, pokud se používá ukazatel na rámec, bez měřítka rámec ukazatele.|  
|. PUSHFRAME [kód]|Generuje položku UWOP_PUSH_MACHFRAME unwind kódu. Pokud je zadán kód volitelné, je zadána položka kódu unwind Modifikátor 1. V opačném případě Modifikátor je 0.|  
|.ENDPROLOG|Označuje konec prologu deklarace.  V první 255 bajty funkce, musí dojít.|  
  
 Tady je ukázkový prolog funkce s správné použití většinu operačních kódů:  
  
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