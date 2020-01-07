---
title: GOTO (MASM)
ms.date: 12/16/2019
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: f198658f9a4b85e0b5ec9b7a0c122241e57286f6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317276"
---
# <a name="goto"></a>GOTO

Převede sestavení na řádek s označením **:** _macrolabel_.

## <a name="syntax"></a>Syntaxe

> **Goto** *macrolabel*

## <a name="remarks"></a>Poznámky

**Příkaz goto** je povolen pouze uvnitř [makra](macro.md), [pro](for-masm.md), [hrnuté](forc.md), [Repeat](repeat.md)a [while](while-masm.md) . Cílem *macrolabel* musí být jediná direktiva na řádku a musí předcházet přední dvojtečka.

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
