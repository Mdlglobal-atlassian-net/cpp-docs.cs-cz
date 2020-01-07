---
title: OPTION (MASM)
ms.date: 12/17/2019
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: bd50ac2e051db7f02ac077054e5856524745df54
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318745"
---
# <a name="option"></a>OPTION

Povolí nebo zakáže funkce assembleru.

## <a name="syntax"></a>Syntaxe

> **Možnost** *optionlist*

## <a name="remarks"></a>Poznámky

Mezi dostupné možnosti patří:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**HLAVNÍ**|
|**Neemulátor**|**EPILOGU**|**EXPR16**|**EXPR32**|
|**LANGUAGE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**KLÍČOVÉ slovo**|**NOSIGNEXTEND**|**OFFSET**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGU**|**READONLY**|**JEN pro čtení**|
|**OBOR**|**Bez oboru**|**SEGMENT**|**SETIF2**.|

Syntaxe jazyka je **jazyk možností:**<em>x</em>, kde *x* je jedna z jazyka C, syscall, STDCALL, Pascal, FORTRAN nebo Basic.  SYSCALL, PASCAL, FORTRAN a BASIC nejsou podporovány v [. MODEL](dot-model.md) je plochý.

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
