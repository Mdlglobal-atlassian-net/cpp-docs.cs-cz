---
title: . PUSHFRAME | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .PUSHFRAME
dev_langs:
- C++
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66531207d21bb7e9e0c165db135f5a0c0d77e478
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053201"
---
# <a name="pushframe"></a>.PUSHFRAME
Generuje `UWOP_PUSH_MACHFRAME` unwind položku kódu. Pokud volitelné `code` je zadána položka unwind kód je zadána Modifikátor 1. V opačném případě Modifikátor je 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.PUSHFRAME [code]  
```  
  
## <a name="remarks"></a>Poznámky  
 . PUSHFRAME umožňuje uživatelům ml64.exe zadejte, jak funkce rámce unwinds a je povoleno pouze v rámci prologu, která rozšiřuje z [PROC](../../assembler/masm/proc.md) deklarace rámce k [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) – direktiva. Tyto direktivy nevydávají kódu; generují pouze `.xdata` a `.pdata`. . PUSHFRAME musí předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. Je dobrým zvykem direktivy unwind a kód, který se mají unwind v makru k zajištění dohody jej.  
  
 Další informace najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)