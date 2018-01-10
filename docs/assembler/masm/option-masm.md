---
title: "MOŽNOST (MASM) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: option
dev_langs: C++
helpviewer_keywords: OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f449606b143bfbf188e878b261f3d35017846862
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="option-masm"></a>OPTION (MASM)
Povolí nebo zakáže funkce assembleru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OPTION   
optionlist  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Mezi dostupné možnosti patří:  
  
|||||  
|-|-|-|-|  
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULÁTOR**|  
|**NOEMULATOR**|**EPILOGU**|**EXPR16**|**EXPR32**|  
|**JAZYK**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**POSUNUTÍ**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**PROLOGU**|**JEN PRO ČTENÍ**|**NOREADONLY**|  
|**OBOR**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|  
  
 Syntaxe pro jazyk je **možnost jazyk:***x*, kde *x* je jedním z C, SYSCALL, STDCALL, PASCAL, FORTRAN nebo BASIC.  SYSCALL, PASCAL, FORTRAN a BASIC nepodporuje použít s [. MODEL](../../assembler/masm/dot-model.md) ploché.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)