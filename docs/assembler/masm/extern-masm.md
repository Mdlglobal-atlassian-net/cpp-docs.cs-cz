---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: fc66338d90b54ecb12ef3ab1aa56214fb445cb13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397565"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Definuje jednu nebo více externích proměnných, popisků nebo symbolů nazvaných *název* , jejichž typ je *typ*.

## <a name="syntax"></a>Syntaxe

> **Extern** ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ⟦ __,__ ⟦*Language-Type*⟧ *Name* ⟦ __(__ *altid* __)__ ⟧ __:__ *Type* ... ⟧

## <a name="remarks"></a>Poznámky

*Typ* může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstantu. Stejné jako [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)
