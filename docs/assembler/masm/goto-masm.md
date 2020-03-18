---
title: GOTO (MASM)
ms.date: 12/16/2019
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 18f286d8634202b57dea788aa6984755a5afb197
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440804"
---
# <a name="goto"></a>GOTO

Převede sestavení na řádek s označením **:** _macrolabel_.

## <a name="syntax"></a>Syntaxe

> **Goto** *macrolabel*

## <a name="remarks"></a>Poznámky

**Příkaz goto** je povolen pouze uvnitř [makra](macro.md), [pro](for-masm.md), [hrnuté](forc.md), [Repeat](repeat.md)a [while](while-masm.md) . Cílem *macrolabel* musí být jediná direktiva na řádku a musí předcházet přední dvojtečka.

## <a name="see-also"></a>Viz také

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
