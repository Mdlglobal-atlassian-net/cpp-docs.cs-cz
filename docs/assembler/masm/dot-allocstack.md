---
title: . ALLOCSTACK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .ALLOCSTACK
dev_langs: C++
helpviewer_keywords: .ALLOCSTACK directive
ms.assetid: 9801594b-7ac2-4df2-a49d-07d9dd9af99e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 20d9147b2c1a95d4fc9600935111a9c0c013be21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="allocstack"></a>.ALLOCSTACK
Generuje **UWOP_ALLOC_SMALL** nebo **UWOP_ALLOC_LARGE** se zadanou velikostí pro aktuální posun v prologu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.ALLOCSTACK size  
```  
  
## <a name="remarks"></a>Poznámky  
 MASM vybere nejvíc efektivní kódování na danou velikost.  
  
 . ALLOCSTACK umožňuje uživatelům ml64.exe zadejte, jak funkce rámce unwinds a je povoleno pouze v rámci prologu, která rozšiřuje z [PROC](../../assembler/masm/proc.md) deklarace rámce k [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) – direktiva. Tyto direktivy nevydávají kódu; generují pouze `.xdata` a `.pdata`. . ALLOCSTACK musí předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. Je dobrým zvykem direktivy unwind a kód, který se mají unwind v makru k zajištění dohody jej.  
  
 `size` Operand musí být násobkem 8.  
  
 Další informace naleznete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="sample"></a>Ukázka  
 Následující příklad ukazuje, jak určit obslužnou rutinu unwind/výjimky:  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)