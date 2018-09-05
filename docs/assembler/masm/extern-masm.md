---
title: EXTERN (MASM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9008e8c1153c0a9b06530b14e661436f7e62a9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693667"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Určuje jeden nebo více externích proměnných, popisky nebo symboly volá *název* jehož typ je *typ*.

## <a name="syntax"></a>Syntaxe

> EXTERN [[*langtype*]] *název* [[(*altid*)]]: *typ* [[, [[*langtype*]]  *název* [[(*altid*)]]: *typ*]]...

## <a name="remarks"></a>Poznámky

*Typ* může být [ABS](../../assembler/masm/operator-abs.md), který importuje *název* jako konstanta. Stejné jako [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>