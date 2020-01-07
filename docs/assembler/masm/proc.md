---
title: PROC
ms.date: 12/06/2019
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: 85d9a1e82eebcd83cb0f12f5ca751ec9415af18d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318667"
---
# <a name="proc"></a>PROC

Označí začátek a konec bloku procedury s názvem *Label*. Příkazy v bloku lze volat pomocí instrukcí **volání** nebo direktivy [Invoke](invoke.md) .

## <a name="syntax"></a>Syntaxe

> *jmenovka* **proc** ⟦*Distance*⟧ *⟦ Language-Type*⟧ ⟦ **Public** | **Private** | **Export** ⟧ __⟦\<__ *prologuearg* __>__ ⟧ ⟦**používá** *reglist ⟧ ⟦* __,__ *parametr* ⟦ __:__ *tag*⟧... ⟧\
> ⟦**Frame** ⟦ __:__ *ehandler-Address*⟧ ⟧ \
> \ *příkazů*
> **ENDP** popisku

## <a name="remarks"></a>Poznámky

Argumenty ⟧ ⟦*Distance*⟧ a ⟦*Language-Type*jsou platné pouze v 32-bit MASM.

⟦**Frame** ⟦ __:__ *ehandler-Address*⟧ ⟧ je platná pouze pro ml64. exe a způsobí, že MASM vygeneruje položku tabulky funkce v. pdata a unwind informace v souboru. xdata pro zpracování chování unwind pro strukturované výjimky funkce.

Pokud je použit atribut **Frame** , musí následovat po [. ](dot-endprolog.md)Direktiva ENDPROLOG

Další informace o použití ml64. exe najdete v tématu [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md) .

## <a name="example"></a>Příklad

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

Výše uvedený kód generuje následující tabulku funkcí a informace o unwind:

```Output
FileHeader->Machine 34404
Dumping Unwind Information for file ex2.exe

.pdata entry 1 0x00001000 0x00001023

  Unwind data: 0x00002000

    Unwind version: 1
    Unwind Flags: None
    Size of prologue: 0x08
    Count of codes: 3
    Frame register: rbp
    Frame offset: 0x0
    Unwind codes:

      Code offset: 0x08, SET_FPREG, register=rbp, offset=0x00
      Code offset: 0x05, ALLOC_SMALL, size=0x10
      Code offset: 0x01, PUSH_NONVOL, register=rbp
```

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
