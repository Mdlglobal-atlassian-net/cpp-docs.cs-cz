---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 424ff295fe37e7c5ff02897a01b99a7c75876f85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397486"
---
# <a name="goto-masm"></a>GOTO (MASM)

Převede sestavení na řádek s označením **:** _macrolabel_.

## <a name="syntax"></a>Syntaxe

> **Goto** *macrolabel*

## <a name="remarks"></a>Poznámky

**Příkaz goto** je povolen pouze uvnitř [makra](macro.md), [pro](for-masm.md), [hrnuté](forc.md), [Repeat](repeat.md)a [while](while-masm.md) . Cílem *macrolabel* musí být jediná direktiva na řádku a musí předcházet přední dvojtečka.

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
