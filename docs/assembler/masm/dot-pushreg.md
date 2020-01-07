---
title: .PUSHREG
ms.date: 12/16/2019
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: de6ffd3668f47732144e8c632410f6dfde6b2f31
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318290"
---
# <a name="pushreg"></a>.PUSHREG

Vygeneruje položku `UWOP_PUSH_NONVOL` unwind kódu pro zadané číslo registru pomocí aktuálního posunu v prologu.

## <a name="syntax"></a>Syntaxe

> . PUSHREG *registraci*

## <a name="remarks"></a>Poznámky

**. PUSHREG** umožňuje uživatelům ml64. exe určit, jak se funkce rámce odvíjí, a je povoleno pouze v prologu, které se rozšíří z deklarace snímku [proc](proc.md) na [. ](dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. **. PUSHREG** by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je vhodné zabalit jak direktivy unwind, tak kód, který mají být určeny k tomu, aby se zajistila shoda.

*registr* může být jeden z těchto: \
RAX | RCX | RDX | RBX | RDI | RSI | RBP | R8 | R9 | R10 | R11 | R12 | R13 | R14 | R15.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ukázka

### <a name="description"></a>Popis

Následující příklad ukazuje, jak nabízet jiné než nestálé Registry.

### <a name="code"></a>Kód

```asm
; ml64 ex1.asm /link /entry:Example1 /SUBSYSTEM:CONSOLE
_text SEGMENT
Example1 PROC FRAME
   push r10
.pushreg r10
   push r15
.pushreg r15
   push rbx
.pushreg rbx
   push rsi
.pushreg rsi
.endprolog
   ; rest of function ...
   ret
Example1 ENDP
_text ENDS
END
```

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
