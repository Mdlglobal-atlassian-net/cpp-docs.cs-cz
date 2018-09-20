---
title: 3.1.9 omp_set_nested – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68e5898b8b57814a152ca2ce9ced84a9df8190cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414534"
---
# <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested – funkce

**Omp_set_nested –** funkce povolí nebo zakáže vnořené paralelismu. Formát je následujícím způsobem:

```
#include <omp.h>
void omp_set_nested(int nested);
```

Pokud *vnořené* vyhodnocen na hodnotu 0, vnořené paralelismu zakázána, což je výchozí a vnořené paralelních oblastí jsou serializovat a spuštění aktuálního vlákna. Pokud *vnořené* vyhodnotí na nenulovou hodnotu, je povoleno vnořené paralelismu a paralelních oblastí, které jsou vnořené můžou nasadit další vlákna do formulářů vnořeného týmy.

Tato funkce má důsledky je popsáno výše, při volání z část programu, kde **omp_in_parallel** vrátí funkce hodnotu nula. Pokud je volána z část programu, kde **omp_in_parallel** funkce vrátí nenulovou hodnotu, nedefinované chování této funkce.

Toto volání má vyšší prioritu než **OMP_NESTED** proměnné prostředí.

Pokud je povoleno vnořené paralelismu, počet podprocesů používaný k provedení vnořených paralelních oblastí je definované implementací. V důsledku toho jsou povoleny OpenMP vyhovující implementace k serializaci vnořených paralelních oblastí, i když je povolena vnořené paralelismu.

## <a name="cross-references"></a>Křížové odkazy:

- **OMP_NESTED** proměnné, viz prostředí [části 4.4](../../parallel/openmp/4-4-omp-nested.md) na stránce 49.

- **omp_in_parallel** funkce naleznete v tématu [části 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stránce 38.