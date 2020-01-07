---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 681c4091a3c54a781bed4b01b235dfeb04f552c6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318095"
---
# <a name="extern"></a>EXTERN

Definuje jednu nebo více externích proměnných, popisků nebo symbolů nazvaných *název* , jejichž typ je *typ*.

## <a name="syntax"></a>Syntaxe

> **Extern** ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Poznámky

Argument *Language-Type* je platný pouze v 32 bitové MASM.

*Typ* může být [ABS](operator-abs.md), který importuje *název* jako konstantu. Stejné jako [EXTRN](extrn.md).

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
