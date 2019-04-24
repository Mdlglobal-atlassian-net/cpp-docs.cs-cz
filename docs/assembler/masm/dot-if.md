---
title: .IF
ms.date: 08/30/2018
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: cf9c594d843c937dd2191bee2a7cebadbc615c82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62185264"
---
# <a name="if"></a>.IF

Generuje kód, který testuje `condition1` (například AX > 7) a spustí *příkazy* při splnění této podmínky.

## <a name="syntax"></a>Syntaxe

> . Pokud condition1<br/>
> příkazy<br/>
> [[. ELSEIF condition2<br/>
> příkazy]]<br/>
> [[.ELSE<br/>
> příkazy]]<br/>
> .ENDIF

## <a name="remarks"></a>Poznámky

Pokud [. OSTATNÍ](../../assembler/masm/dot-else.md) způsobem, jeho příkazy se spustí, pokud byl původní podmínky hodnotu false. Všimněte si, že podmínky se vyhodnocují v době běhu.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>