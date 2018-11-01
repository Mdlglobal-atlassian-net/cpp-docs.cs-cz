---
title: .DOSSEG
ms.date: 08/30/2018
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 28b3e351030ee83693c0fec5568aacf9b4b77c27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639436"
---
# <a name="dosseg"></a>.DOSSEG

Seřadí segmentů podle úmluvy segmentu zástupného kódu MS-DOS: kód nejprve pak segmenty nejsou v DGROUP a potom segmenty v DGROUP.

## <a name="syntax"></a>Syntaxe

> .DOSSEG

## <a name="remarks"></a>Poznámky

Toto pořadí podle segmentů v DGROUP: segmenty nejsou v BSS nebo zásobníku, pak BSS segmentů a nakonec zásobníku segmentů. Používá se především pro zajištění podpory CodeView v programech samostatného MASM. Stejné jako [DOSSEG](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>