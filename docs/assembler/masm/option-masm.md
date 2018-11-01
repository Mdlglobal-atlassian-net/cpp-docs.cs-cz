---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: a8215bf1f816baa490a768fb2cab0b3c2e53e20b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596479"
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