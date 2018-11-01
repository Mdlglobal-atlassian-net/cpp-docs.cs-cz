---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 23d34af470e825a8535de8cb28645a7bfb4c4d1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619762"
---
# <a name="externdef"></a>EXTERNDEF

Určuje jeden nebo více externích proměnných, popisky nebo symboly volá *název* jehož typ je `type`.

## <a name="syntax"></a>Syntaxe

> EXTERNDEF [[langtype]]. název: Typ [[, název: Typ [[langtype]]]]...

## <a name="remarks"></a>Poznámky

Pokud *název* je definována v modulu je považován za [veřejné](../../assembler/masm/public-masm.md). Pokud *název* se odkazuje v modulu je považován za [EXTERN](../../assembler/masm/extern-masm.md). Pokud *název* se neodkazuje, je ignorována. `type` Může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstanta. Obvykle se používá v soubory k zahrnutí.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>