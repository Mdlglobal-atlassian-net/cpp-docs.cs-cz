---
title: . POKUD | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7bd5ba5821b4dcfb2d088e31816f50540445018
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691541"
---
# <a name="if"></a>.IF

Generuje kód, který testuje `condition1` (například AX > 7) a spustí *příkazy* při splnění této podmínky.

## <a name="syntax"></a>Syntaxe

> . Pokud condition1<br/>
> příkazy<br/>
> [[. ELSEIF condition2<br/>
> příkazy]]<br/>
> [[. ELSE<br/>
> příkazy]]<br/>
> .ENDIF

## <a name="remarks"></a>Poznámky

Pokud [. OSTATNÍ](../../assembler/masm/dot-else.md) způsobem, jeho příkazy se spustí, pokud byl původní podmínky hodnotu false. Všimněte si, že podmínky se vyhodnocují v době běhu.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>