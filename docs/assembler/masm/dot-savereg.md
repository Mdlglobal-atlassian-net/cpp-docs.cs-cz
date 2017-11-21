---
title: . SAVEREG | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .SAVEREG
dev_langs: C++
helpviewer_keywords: .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e55abe8a5661184b022fad3f6a50dc9813cae9d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="savereg"></a>.SAVEREG
Generuje buď `UWOP_SAVE_NONVOL` nebo `UWOP_SAVE_NONVOL_FAR` unwind položku kódu pro zadaný registr (`reg`) a posunutí (`offset`) pomocí aktuální posun prologu. MASM vybere nejúčinnější kódování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.SAVEREG reg, offset  
```  
  
## <a name="remarks"></a>Poznámky  
 . SAVEREG umožňuje uživatelům ml64.exe zadejte, jak funkce rámce unwinds a je povoleno pouze v rámci prologu, která rozšiřuje z [PROC](../../assembler/masm/proc.md) deklarace rámce k [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) – direktiva. Tyto direktivy nevydávají kódu; generují pouze `.xdata` a `.pdata`. . SAVEREG musí předcházet pokyny, které ve skutečnosti implementovat akce, jež mají být oddělen. Je dobrým zvykem direktivy unwind a kód, který se mají unwind v makru k zajištění dohody jej.  
  
 Další informace najdete v tématu [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)