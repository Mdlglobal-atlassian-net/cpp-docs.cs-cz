---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: ed7b9e63bb19dcc16539dbdaaf1f6a7f16566b3c
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397453"
---
# <a name="if-masm"></a>IF (MASM)

Udělí sestavení *ifstatements* , je-li hodnota *expression1* true (nenulová) nebo *elseifstatements* , pokud je hodnota *Výraz1* false (0) a vlastnost *Výraz2* je true.

## <a name="syntax"></a>Syntaxe

> **If** *Výraz1*\
> *příkazy if*\
> ⟦**ElseIf** *Výraz2*\
> *ElseIf-příkazy*⟧ \
> ⟦**ELSE**\
> *else-příkazy*⟧ \
> **ENDIF**

## <a name="remarks"></a>Poznámky

Pro [ElseIf](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **elseifdef –** , **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**a **elseifndef –** mohou být nahrazeny následující direktivy. Volitelně sestaví *Další příkazy* , pokud je předchozí výraz nepravdivý. Všimněte si, že výrazy jsou vyhodnocovány v době sestavení.

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
