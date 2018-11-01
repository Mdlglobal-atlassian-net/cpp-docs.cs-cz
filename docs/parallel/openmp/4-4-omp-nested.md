---
title: 4.4 OMP_NESTED
ms.date: 11/04/2016
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
ms.openlocfilehash: e45b8901c56923ab37ca387a5f057c5b41af21f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453618"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED` Proměnnou prostředí povolí nebo zakáže vnořené paralelismu, pokud je povoleno nebo zakázáno voláním vnořené paralelismu `o` **mp_set_nested** rutina knihovny. Pokud nastavena na **TRUE**, vnořené paralelismu je povolené; Pokud je nastavena na **FALSE**vnořené paralelismu je zakázaná. Výchozí hodnota je **FALSE**.

Příklad:

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>Křížový odkaz:

- `omp_set_nested` Funkce, najdete v článku [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40.