---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 83c9ff588e2fe273e24e1d0b1c16517c5eee3365
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703783"
---
# <a name="if-32-bit-masm"></a>. IF (32-bit MASM)

Vygeneruje kód, který testuje `condition1` (například AX > 7) a provede *příkazy* , pokud je tato podmínka pravdivá. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> . Pokud condition1<br/>
> příkazy<br/>
> [[. ELSEIF Podmínka2<br/>
> příkazy]]<br/>
> [[. OSTATNÍCH<br/>
> příkazy]]<br/>
> .ENDIF

## <a name="remarks"></a>Poznámky

Pokud [. V OPAČNém](../../assembler/masm/dot-else.md) případě se spustí jeho příkazy, pokud původní podmínka byla nepravdivá. Všimněte si, že podmínky jsou vyhodnocovány v době běhu.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>