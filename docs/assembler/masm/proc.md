---
title: PROC
ms.date: 08/30/2018
f1_keywords:
- PROC
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
ms.openlocfilehash: e7931c97570c0fefcacb0123d75934867793fba4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62210531"
---
# <a name="proc"></a>PROC

Označuje začátek a konec bloku procedura volána *popisek*. Příkazy v bloku nelze volat s **volání** instrukce nebo [INVOKE](../../assembler/masm/invoke.md) směrnice.

## <a name="syntax"></a>Syntaxe

> *Popisek* PROC [[*vzdálenost*]] [[*langtype*]] [[*viditelnost*]] [[\<*prologuearg*>]] [[ POUŽÍVÁ *reglist*]] [[, *parametr* [[:*značka*]]]...<br/>
> [[SNÍMKU [[:*ehandler adresu*]]]]<br/>
> *Příkazy*<br/>
> *Popisek* ENDP

## <a name="remarks"></a>Poznámky

[[SNÍMKU [[:*ehandler adresu*]]]] je platný pouze s ml64.exe a způsobí, že MASM pro generování záznam tabulky funkcí v .pdata a vrátit se zpět informace v .xdata funkce uživatele strukturované zpracování výjimek unwind chování.

Když **rámce** atribut se používá, musí být následován znakem [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) směrnice.

Zobrazit [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md) pro další informace o použití ml64.exe.

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

Ve výše uvedeném kódu bude generovat v následující tabulce funkce a unwind informace:

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

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>