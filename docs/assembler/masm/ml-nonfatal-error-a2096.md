---
title: Méně závažná chyba nástroje ML A2096
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: 425e99c1dc6675e8b970433948e0cc09b8d54485
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312661"
---
# <a name="ml-nonfatal-error-a2096"></a>Méně závažná chyba nástroje ML A2096

**byl očekáván segment, skupina nebo segment registru.**

Byl očekáván segment nebo skupina, ale nebyl nalezen.

Došlo k jedné z následujících:

- Levý operand zadaný pomocí operátoru přepisu segmentu ( **:** ) nebyl registr segmentů (cs, DS, SS, ES, FS nebo GS), název skupiny, název segmentu nebo výraz segmentu.

- Direktivě [Přepokládejme](assume.md) byl přidělen registr segmentu bez platné adresy segmentu, registru segmentu, skupiny nebo speciální **ploché** skupiny.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
