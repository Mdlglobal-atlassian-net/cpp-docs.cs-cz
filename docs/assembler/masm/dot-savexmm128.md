---
title: . SAVEXMM128 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAVEXMM128
dev_langs: C++
helpviewer_keywords: .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 384615a0c58c3c28a2e0958d6909546f5753ce6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="savexmm128"></a>.SAVEXMM128
Generuje buď `UWOP_SAVE_XMM128` nebo `UWOP_SAVE_XMM128_FAR` unwind položku kódu pro zadaný XMM registr a posun pomocí aktuální posun prologu. MASM vybere nejúčinnější kódování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.savexmm128 xmmreg , offset  
```  
  
## <a name="remarks"></a>Poznámky  
 . SAVEXMM128 umožňuje uživatelům ml64.exe zadejte, jak funkce rámce unwinds a je povoleno pouze v rámci prologu, která rozšiřuje z [PROC](../../assembler/masm/proc.md) deklarace rámce k [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) – direktiva. Tyto direktivy nevydávají kódu; generují pouze `.xdata` a `.pdata`. . SAVEXMM128 musí předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. Je dobrým zvykem direktivy unwind a kód, který se mají unwind v makru k zajištění dohody jej.  
  
 `offset`musí být násobkem 16.  
  
 Další informace najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)