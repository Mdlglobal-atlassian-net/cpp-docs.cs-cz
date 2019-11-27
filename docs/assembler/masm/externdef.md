---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 469b49832c171ee78336a0c457f0d269acd3b59d
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397531"
---
# <a name="externdef"></a>EXTERNDEF

Definuje jednu nebo více externích proměnných, popisků nebo symbolů nazvaných *název* , jejichž typ je *typ*.

## <a name="syntax"></a>Syntaxe

> **EXTERNDEF** ⟦*typu jazyka* *⟧* __:__ *Zadejte* ⟦ __,__ ⟦*jazyk-typ*⟧ *název* __:__ *typ* ... ⟧

## <a name="remarks"></a>Poznámky

Pokud je *název* definován v modulu, je považován za [veřejný](../../assembler/masm/public-masm.md). Pokud je v modulu odkazováno na *název* , je považován za [extern](../../assembler/masm/extern-masm.md). Pokud na *název* neodkazuje, bude ignorován. *Typ* může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstantu. Obvykle používáno v zahrnutých souborech.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)
