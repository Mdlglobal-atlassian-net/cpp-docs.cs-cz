---
title: .SETFRAME
ms.date: 08/30/2018
f1_keywords:
- .SETFRAME
helpviewer_keywords:
- .SETFRAME directive
ms.assetid: eaa9b5ed-4daa-4f1e-bdb6-100758007ab3
ms.openlocfilehash: a21dda496d32abcfeb4692d0228afdbcfd4e5ebb
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397921"
---
# <a name="setframe"></a>.SETFRAME

Vyplní pole registru rámce a posune v informacích o unwind pomocí zadaného registru (*reg*) a posunutí (*posun*). Posun musí být násobkem 16 a menší nebo roven 240. Tato direktiva také generuje položku `UWOP_SET_FPREG` unwind kódu pro zadaný registr pomocí aktuálního posunu prologu.

## <a name="syntax"></a>Syntaxe

> **. SETFRAME** *reg*, *offset*

## <a name="remarks"></a>Poznámky

**. SETFRAME** umožňuje uživatelům ml64. exe určit, jak se funkce rámce odvíjí, a je povoleno pouze v prologu, které se rozšíří z deklarace snímku [proc](../../assembler/masm/proc.md) na [. ](../../assembler/masm/dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. **. SETFRAME** by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je vhodné zabalit jak direktivy unwind, tak kód, který mají být určeny k tomu, aby se zajistila shoda.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ukázka

### <a name="description"></a>Popis

Následující příklad ukazuje, jak použít ukazatel na rámec:

### <a name="code"></a>Kód

```asm
; ml64 frmex2.asm /link /entry:frmex2 /SUBSYSTEM:CONSOLE
_text SEGMENT
frmex2 PROC FRAME
   push rbp
.pushreg rbp
   sub rsp, 010h
.allocstack 010h
   mov rbp, rsp
.setframe rbp, 0
.endprolog
   ; modify the stack pointer outside of the prologue (similar to alloca)
   sub rsp, 060h

   ; we can unwind from the following AV because of the frame pointer
   mov rax, 0
   mov rax, [rax] ; AV!

   add rsp, 060h
   add rsp, 010h
   pop rbp
   ret
frmex2 ENDP
_text ENDS
END
```

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
