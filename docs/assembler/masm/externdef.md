---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 23d34af470e825a8535de8cb28645a7bfb4c4d1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203085"
---
# <a name="externdef"></a>EXTERNDEF

Určuje jeden nebo více externích proměnných, popisky nebo symboly volá *název* jehož typ je `type`.

## <a name="syntax"></a>Syntaxe

> EXTERNDEF [[langtype]]. název: Typ [[, název: Typ [[langtype]]]]...

## <a name="remarks"></a>Poznámky

Pokud *název* je definována v modulu je považován za [veřejné](../../assembler/masm/public-masm.md). Pokud *název* se odkazuje v modulu je považován za [EXTERN](../../assembler/masm/extern-masm.md). Pokud *název* se neodkazuje, je ignorována. `type` Může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstanta. Obvykle se používá v soubory k zahrnutí.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>