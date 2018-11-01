---
title: 4.1 OMP_SCHEDULE
ms.date: 11/04/2016
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
ms.openlocfilehash: 4731299a4f7203dd01f660ea25bf2f5b58060630
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432692"
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

**OMP_SCHEDULE** platí jenom pro **pro** a **paralelní pro** direktivy, které mají typ plánu **runtime**. Plán typ a bloků velikosti takové smyčky lze nastavit v době běhu pomocí nastavení této proměnné prostředí na některý z typů rozpoznaný plánu a volitelně *chunk_size*.

Pro **pro** a **paralelní pro** direktivy, které mají typ plánu jiné než **runtime**, **OMP_SCHEDULE** se ignoruje. Výchozí hodnota pro tuto proměnnou prostředí je definován implementací. Pokud volitelný *chunk_size* nastaven, hodnota musí být kladná. Pokud *chunk_size* není nastaven, je použita hodnota 1, s výjimkou v případě třídy **statické** plánu. Pro **statické** , výchozí velikost bloku je naplánováno do prostoru iterace smyčky vydělí počtem vláken u smyčky.

Příklad:

```
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

## <a name="cross-references"></a>Křížové odkazy:

- **pro** direktiv, viz [části 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stránce 11.

- **paralelní pro** direktiv, viz [části 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) na stránce 16.