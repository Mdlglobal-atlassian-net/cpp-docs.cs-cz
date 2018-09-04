---
title: . ALLOCSTACK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .ALLOCSTACK
dev_langs:
- C++
helpviewer_keywords:
- .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 292a7fcdb0a1d7c4ecccab895c643479397b4a98
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681928"
---
# <a name="allocstack"></a>.ALLOCSTACK

Generuje **UWOP_ALLOC_SMALL** nebo **UWOP_ALLOC_LARGE** se zadanou velikostí pro aktuální posun v prologu.

## <a name="syntax"></a>Syntaxe

> . Velikost ALLOCSTACK

## <a name="remarks"></a>Poznámky

MASM zvolí nejúčinnější kódování pro danou velikost.

. ALLOCSTACK umožňuje uživatelům ml64.exe k určení, jak funkce rámce unwinds a je povolený jenom v rámci prologu, který se táhne od [PROC](../../assembler/masm/proc.md) prohlášení rámce [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) směrnice. Tyto direktivy negeneruje kód; pouze generovat `.xdata` a `.pdata`. . ALLOCSTACK by měl předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. To je dobrý postup při zabalení direktivy unwind a kódu, které jsou určeny k unwind v makru zajistit smlouvy.

`size` Operand musí být násobkem 8.

Další informace najdete v článku [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="sample"></a>Ukázka

Následující příklad ukazuje, jak určit obslužné rutiny výjimky nebo unwind:

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

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>