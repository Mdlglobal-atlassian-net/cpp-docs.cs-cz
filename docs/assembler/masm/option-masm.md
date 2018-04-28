---
title: MOŽNOST (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80291c805cad3ef041fffc58983ff399da07c9d9
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
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
  
 Syntaxe pro jazyk je **možnost jazyk: *** x*, kde *x* je jedním z C, SYSCALL, STDCALL, PASCAL, FORTRAN nebo BASIC.  SYSCALL, PASCAL, FORTRAN a BASIC nepodporuje použít s [. MODEL](../../assembler/masm/dot-model.md) ploché.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)