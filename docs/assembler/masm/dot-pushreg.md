---
title: . PUSHREG | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .PUSHREG
dev_langs:
- C++
helpviewer_keywords:
- .PUSHREG directive
ms.assetid: e0c83758-dfed-40ea-afe6-cb833c8d2d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4b9f4a7189d2dbe3717535a95a1816e5fd0de3b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055144"
---
# <a name="pushreg"></a>.PUSHREG
Generuje `UWOP_PUSH_NONVOL` unwind položka kód pro zadané číslo, které používá aktuální posun v prologu registru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.PUSHREG register  
```  
  
## <a name="remarks"></a>Poznámky  
 . PUSHREG umožňuje uživatelům ml64.exe zadejte, jak funkce rámce unwinds a je povoleno pouze v rámci prologu, která rozšiřuje z [PROC](../../assembler/masm/proc.md) deklarace rámce k [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) – direktiva. Tyto direktivy nevydávají kódu; generují pouze `.xdata` a `.pdata`. . PUSHREG musí předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. Je dobrým zvykem direktivy unwind a kód, který se mají unwind v makru k zajištění dohody jej.  
  
 Další informace najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="sample"></a>Ukázka  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje, jak push tegisters stálé.  
  
### <a name="code"></a>Kód  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)