---
title: PROC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PROC
dev_langs:
- C++
helpviewer_keywords:
- PROC directive
ms.assetid: ee5bb6b6-fa15-4d73-b0cf-e650178539a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ee26e181f0f40126c86a36889c43405f0b40f5e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680843"
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