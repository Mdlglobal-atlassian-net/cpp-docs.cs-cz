---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: e757781151bd1bb57940e5c54f7333a5daa93c74
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987893"
---
# <a name="externdef"></a>EXTERNDEF

Definuje jednu nebo více externích proměnných, popisků nebo symbolů nazvaných *název* , jejichž typ je *typ*.

## <a name="syntax"></a>Syntaxe

> **EXTERNDEF** ⟦*typu jazyka* *⟧* __:__ *Zadejte* ⟦ __,__ ⟦*jazyk-typ*⟧ *název* __:__ *typ* ... ⟧

## <a name="remarks"></a>Poznámky

Argument *Language-Type* je platný pouze v 32 bitové MASM.

Pokud je *název* definován v modulu, je považován za [veřejný](../../assembler/masm/public-masm.md). Pokud je v modulu odkazováno na *název* , je považován za [extern](../../assembler/masm/extern-masm.md). Pokud na *název* neodkazuje, bude ignorován. *Typ* může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstantu. Obvykle používáno v zahrnutých souborech.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)
