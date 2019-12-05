---
title: Méně závažná chyba nástroje ML A2096
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: 14fb30214cf7badf51368672dc52635d50a067f1
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855471"
---
# <a name="ml-nonfatal-error-a2096"></a>Méně závažná chyba nástroje ML A2096

**byl očekáván segment, skupina nebo segment registru.**

Byl očekáván segment nebo skupina, ale nebyl nalezen.

Došlo k jedné z následujících:

- Levý operand zadaný pomocí operátoru přepisu segmentu ( **:** ) nebyl registr segmentů (cs, DS, SS, ES, FS nebo GS), název skupiny, název segmentu nebo výraz segmentu.

- Direktivě [Přepokládejme](../../assembler/masm/assume.md) byl přidělen registr segmentu bez platné adresy segmentu, registru segmentu, skupiny nebo speciální **ploché** skupiny.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>