---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 17edea122afc03a8c3a2fdc86ee6c06c2ccf3c85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398492"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG – (32-bit MASM)

Seřadí segmenty podle konvence segmentů pro systém MS-DOS: nejprve CODE, pak segmenty nejsou v DGROUP a pak segmenty v DGROUP. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **.DOSSEG**

## <a name="remarks"></a>Poznámky

Segmenty v DGROUP se řídí tímto pořadím: segmenty nejsou v BSS nebo STACK, pak segmenty BSS a nakonec segmenty zásobníku. Primárně se používá pro zajištění podpory CodeView v samostatných programech MASM. Stejné jako [dosseg –](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)
