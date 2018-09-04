---
title: MOŽNOST (MASM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 09db749baf09525957faaf8af99434cc9775d0e7
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678042"
---
# <a name="option-masm"></a>OPTION (MASM)

Povolí nebo zakáže funkce assembler.

## <a name="syntax"></a>Syntaxe

> MOŽNOST *optionlist*

## <a name="remarks"></a>Poznámky

Mezi dostupné možnosti patří:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULÁTOR**|
|**NOEMULATOR**|**EPILOGU**|**EXPR16**|**EXPR32**|
|**JAZYK**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**POSUN**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGU**|**JEN PRO ČTENÍ**|**NOREADONLY**|
|**OBOR**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|

Syntaxe jazyka je **možností jazyka:**<em>x</em>, kde *x* je jedním z jazyka C, SYSCALL, STDCALL, PASCAL, až po FORTRAN nebo BASIC.  SYSCALL, PASCAL, až po FORTRAN a BASIC nepodporuje použít s [. MODEL](../../assembler/masm/dot-model.md) bez stromové struktury.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>