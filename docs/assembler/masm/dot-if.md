---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: e8213052dce8d84d62f90d4bc2653435c2b31434
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398227"
---
# <a name="if-32-bit-masm"></a>. IF (32-bit MASM)

Vygeneruje kód, který testuje *condition1* (například AX > 7) a provede *příkazy* , pokud je tato podmínka pravdivá. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **. Pokud**\ *condition1*
> \ *příkazů*
> ⟦ **. ELSEIF** *Podmínka2*\
> *příkazy*⟧ \
> ⟦ **. JINAK**\
> *příkazy*⟧ \
> **.ENDIF**

## <a name="remarks"></a>Poznámky

Pokud [. V OPAČNém](../../assembler/masm/dot-else.md) případě se spustí jeho příkazy, pokud původní podmínka byla nepravdivá. Všimněte si, že podmínky jsou vyhodnocovány v době běhu.

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
