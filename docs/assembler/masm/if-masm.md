---
title: POKUD (MASM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74d9d223d12164de6a908159eb0d44ea271b0be5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="if-masm"></a>IF (MASM)
Uděluje sestavením *ifstatements* Pokud *expression1* hodnotu true (nenulové) nebo *elseifstatements* Pokud *expression1* hodnotu false (0) a *Výraz2* hodnotu true.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   IF expression1  
ifstatements  
[[ELSEIF expression2  
   elseifstatements]]  
[[ELSE  
   elsestatements]]  
ENDIF  
```  
  
## <a name="remarks"></a>Poznámky  
 Následující direktivy mohou nahradit [ElseIf –](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **elseifdef –**, **ELSEIFDIF**, **ELSEIFDIFI** , **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**, a **elseifndef –** . Volitelně sestaví *elsestatements* Pokud předchozí výraz je hodnota false. Všimněte si, že výrazy jsou vyhodnocovány v době sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)