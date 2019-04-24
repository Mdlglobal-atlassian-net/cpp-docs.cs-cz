---
title: .PUSHREG
ms.date: 08/30/2018
f1_keywords:
- .PUSHREG
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
ms.openlocfilehash: 19e36f1c0b073c5b174ea9acb0f1eaac7d771c46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203977"
---
# <a name="pushreg"></a>.PUSHREG

Generuje `UWOP_PUSH_NONVOL` unwind vstupní kód pro zadané číslo pomocí aktuální posun v prologu registru.

## <a name="syntax"></a>Syntaxe

> . PUSHREG registru

## <a name="remarks"></a>Poznámky

. PUSHREG umožňuje uživatelům ml64.exe zadejte způsob, jakým funkce rámce unwinds se povoluje jenom v prologu, který se táhne od [PROC](../../assembler/masm/proc.md) prohlášení rámce [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) směrnice. Tyto direktivy negeneruje kód; pouze generovat `.xdata` a `.pdata`. . PUSHREG by měl předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. To je dobrý postup při zabalení direktivy unwind a kódu, které jsou určeny k unwind v makru zajistit smlouvy.

Další informace najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ukázka

### <a name="description"></a>Popis

Následující příklad ukazuje, jak vložit tegisters stálé.

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

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>