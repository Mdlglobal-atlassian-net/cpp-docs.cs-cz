---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 2cc5884a7473da9175a6b6af4b4251314deffeb4
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313389"
---
# <a name="externdef"></a>EXTERNDEF

Definuje jednu nebo více externích proměnných, popisků nebo symbolů nazvaných *název* , jejichž typ je *typ*.

## <a name="syntax"></a>Syntaxe

> **EXTERNDEF** ⟦*typu jazyka* *⟧* __:__ *Zadejte* ⟦ __,__ ⟦*jazyk-typ*⟧ *název* __:__ *typ* ... ⟧

## <a name="remarks"></a>Poznámky

Argument *Language-Type* je platný pouze v 32 bitové MASM.

Pokud je *název* definován v modulu, je považován za [veřejný](public-masm.md). Pokud je v modulu odkazováno na *název* , je považován za [extern](extern-masm.md). Pokud na *název* neodkazuje, bude ignorován. *Typ* může být [ABS](operator-abs.md), který importuje *název* jako konstantu. Obvykle používáno v zahrnutých souborech.

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
