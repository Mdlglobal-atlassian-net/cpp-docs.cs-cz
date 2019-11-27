---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: 0f90ab0115c3dde894d468bbbe60ffa0193b8336
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395171"
---
# <a name="option-masm"></a>OPTION (MASM)

Povolí nebo zakáže funkce assembleru.

## <a name="syntax"></a>Syntaxe

> **Možnost** *optionlist*

## <a name="remarks"></a>Poznámky

K dispozici jsou tyto možnosti:

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**HLAVNÍ**|
|**Neemulátor**|**EPILOGU**|**EXPR16**|**EXPR32**|
|**LANGUAGE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**KLÍČOVÉ slovo**|**NOSIGNEXTEND**|**POLOHY**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGU**|**READONLY**|**JEN pro čtení**|
|**OBOR**|**Bez oboru**|**SEGMENT**|**SETIF2**.|

Syntaxe jazyka je **jazyk možností:** <em>x</em>, kde *x* je jedna z jazyka C, syscall, STDCALL, Pascal, FORTRAN nebo Basic.  SYSCALL, PASCAL, FORTRAN a BASIC nejsou podporovány pro použití s [. MODEL](../../assembler/masm/dot-model.md) je plochý.

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
