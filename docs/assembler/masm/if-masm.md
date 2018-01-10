---
title: POKUD (MASM) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: if
dev_langs: C++
helpviewer_keywords: IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6889f70ce149a03adc47fba48e67dc0b9434473c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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