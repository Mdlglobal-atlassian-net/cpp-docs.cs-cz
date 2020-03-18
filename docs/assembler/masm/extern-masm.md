---
title: EXTERN (MASM)
ms.date: 12/06/2019
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 2674f358fe22f74c5272d90a0d8cbff234ddcd11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440883"
---
# <a name="extern"></a>EXTERN

Definuje jednu nebo více externích proměnných, popisků nebo symbolů nazvaných *název* , jejichž typ je *typ*.

## <a name="syntax"></a>Syntaxe

> **Extern** ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Poznámky

Argument *Language-Type* je platný pouze v 32 bitové MASM.

*Typ* může být [ABS](operator-abs.md), který importuje *název* jako konstantu. Stejné jako [EXTRN](extrn.md).

## <a name="see-also"></a>Viz také

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
