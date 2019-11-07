---
title: .REPEAT
ms.date: 11/05/2019
f1_keywords:
- .REPEAT
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
ms.openlocfilehash: 0533397c60c83f22b10c84ec72aa6eb65a71e4c0
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703569"
---
# <a name="repeat-32-bit-masm"></a>. OPAKOVAT (32-bit MASM)

Vygeneruje kód, který opakuje provádění bloku *příkazů* , dokud `condition` nebude pravda. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), která se bude pravda, když je CX nula, může být nahrazena [. DO](../../assembler/masm/dot-until.md). `condition` je volitelná pro **. UNTILCXZ**. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> .REPEAT<br/>
> příkazy<br/>
> . DO podmínky

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>