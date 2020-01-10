---
title: .ALLOCSTACK
ms.date: 12/17/2019
f1_keywords:
- .ALLOCSTACK
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
ms.openlocfilehash: bcc94619dfa24ab5c8b5d23a60825641290ef176
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314182"
---
# <a name="allocstack"></a>.ALLOCSTACK

Vygeneruje **UWOP_ALLOC_SMALL** nebo **UWOP_ALLOC_LARGE** se zadanou velikostí pro aktuální posun v prologu.

## <a name="syntax"></a>Syntaxe

> **.**  *Velikost* ALLOCSTACK

## <a name="remarks"></a>Poznámky

MASM vybere pro danou velikost nejúčinnější kódování.

**. ALLOCSTACK** umožňuje uživatelům ml64. exe určit způsob, jakým funkce rámce odvíjí a je povolena pouze v prologu, které se rozšíří z deklarace snímku [proc](proc.md) na [. ](dot-endprolog.md)Direktiva ENDPROLOG Tyto direktivy negenerují kód; generují pouze `.xdata` a `.pdata`. **. ALLOCSTACK** by měl předcházet pokyny, které skutečně implementují akce, které se mají oddělit. Je vhodné zabalit jak direktivy unwind, tak kód, který mají být určeny k tomu, aby se zajistila shoda.

Operandem *velikosti* musí být násobek osmi.

Další informace najdete v tématu [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ukázka

Následující příklad ukazuje, jak zadat obslužnou rutinu unwind/Exception:

```asm
; ml64 ex3.asm /link /entry:Example1  /SUBSYSTEM:Console
text SEGMENT
PUBLIC Example3
PUBLIC Example3_UW
Example3_UW PROC NEAR
   ; exception/unwind handler body

   ret 0

Example3_UW ENDP

Example3 PROC FRAME : Example3_UW

   sub rsp, 16
.allocstack 16

.endprolog

   ; function body
    add rsp, 16
   ret 0

Example3 ENDP
text ENDS
END
```

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
