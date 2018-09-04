---
title: EXTERNDEF | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5c3d42cabb88c38ce1d98da24cd2cb4ddec8d5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683658"
---
# <a name="externdef"></a>EXTERNDEF

Určuje jeden nebo více externích proměnných, popisky nebo symboly volá *název* jehož typ je `type`.

## <a name="syntax"></a>Syntaxe

> EXTERNDEF [[langtype]]. název: Typ [[, název: Typ [[langtype]]]]...

## <a name="remarks"></a>Poznámky

Pokud *název* je definována v modulu je považován za [veřejné](../../assembler/masm/public-masm.md). Pokud *název* se odkazuje v modulu je považován za [EXTERN](../../assembler/masm/extern-masm.md). Pokud *název* se neodkazuje, je ignorována. `type` Může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstanta. Obvykle se používá v soubory k zahrnutí.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>