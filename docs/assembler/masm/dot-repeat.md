---
title: . OPAKUJTE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8856ed0e1d86277a413baac2c56e5c5ca2ea9ff0
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "43687949"
---
# <a name="repeat"></a>.REPEAT

Generuje kód, který se opakuje spouštění bloku *příkazy* dokud `condition` stane pravdivou. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), který změní hodnotu true, pokud CX je nula, může být nahrazeno [. DOKUD](../../assembler/masm/dot-until.md). `condition` Je volitelný s **. UNTILCXZ**.

## <a name="syntax"></a>Syntaxe

> .REPEAT<br/>
> příkazy<br/>
> . Až do podmínky

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>