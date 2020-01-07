---
title: Závažná chyba nástroje ML A1010
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1010
helpviewer_keywords:
- A1010
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
ms.openlocfilehash: b3141f8819a33281c70e34bd7772d4475886e557
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312583"
---
# <a name="ml-fatal-error-a1010"></a>Závažná chyba nástroje ML A1010

**nespárované vnořování bloků:**

Blok, který začíná, nemá shodný konec, nebo konec bloku neměl shodný začátek. Může být zahrnuta jedna z následujících možností:

- Direktiva vysoké úrovně, například [. Pokud](dot-if.md), [. Opakujte akci](dot-repeat.md), nebo [. WHILe](dot-while.md).

- Direktiva podmíněného sestavení, například [if](if-masm.md), [Repeat](repeat.md)nebo **while**.

- Definice struktury nebo sjednocení.

- Definice procedury.

- Definice segmentu.

- Direktiva [POPCONTEXT](popcontext.md)

- Direktiva podmíněného sestavení, jako je například [Else](else-masm.md), [ElseIf](elseif-masm.md)nebo **endif** bez odpovídajícího typu [if](if-masm.md).

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
