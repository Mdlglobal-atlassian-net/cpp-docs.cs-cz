---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 6992ec8b151a83b3f9fa920997845c20caf0476d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317744"
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

Pokud [. V OPAČNém](dot-else.md) případě se spustí jeho příkazy, pokud původní podmínka byla nepravdivá. Všimněte si, že podmínky jsou vyhodnocovány v době běhu.

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
