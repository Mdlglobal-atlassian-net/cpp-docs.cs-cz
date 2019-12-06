---
title: Závažná chyba nástroje ML A1010
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: 6ec82f7f6d559d977a9aa039ed91689a0ef4d49a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856875"
---
# <a name="ml-fatal-error-a1010"></a>Závažná chyba nástroje ML A1010

**nespárované vnořování bloků:**

Blok, který začíná, nemá shodný konec, nebo konec bloku neměl shodný začátek. Může být zahrnuta jedna z následujících možností:

- Direktiva vysoké úrovně, například [. Pokud](../../assembler/masm/dot-if.md), [. Opakujte akci](../../assembler/masm/dot-repeat.md), nebo [. WHILe](../../assembler/masm/dot-while.md).

- Direktiva podmíněného sestavení, například [if](../../assembler/masm/if-masm.md), [Repeat](../../assembler/masm/repeat.md)nebo **while**.

- Definice struktury nebo sjednocení.

- Definice procedury.

- Definice segmentu.

- Direktiva [POPCONTEXT](../../assembler/masm/popcontext.md)

- Direktiva podmíněného sestavení, jako je například [Else](../../assembler/masm/else-masm.md), [ElseIf](../../assembler/masm/elseif-masm.md)nebo **endif** bez odpovídajícího typu [if](../../assembler/masm/if-masm.md).

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>