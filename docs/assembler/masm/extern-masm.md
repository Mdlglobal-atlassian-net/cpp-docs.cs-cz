---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 30d1b3ae7c6676aeb97b91c7627da859525b9ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497354"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Určuje jeden nebo více externích proměnných, popisky nebo symboly volá *název* jehož typ je *typ*.

## <a name="syntax"></a>Syntaxe

> EXTERN [[*langtype*]] *název* [[(*altid*)]]: *typ* [[, [[*langtype*]]  *název* [[(*altid*)]]: *typ*]]...

## <a name="remarks"></a>Poznámky

*Typ* může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstanta. Stejné jako [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>