---
title: 4.3 OMP_DYNAMIC
ms.date: 11/04/2016
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
ms.openlocfilehash: 0ea6784159a11fc194d0c1cd16d2316a80b9cd37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488562"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

**OMP_DYNAMIC** proměnnou prostředí povolí nebo zakáže dynamické úpravy počtu vláken, které jsou k dispozici pro provádění paralelních oblastí, pokud není explicitně povoleno nebo zakázáno voláním dynamickéúpravy**omp_set_dynamic –** rutina knihovny. Musí být jeho hodnota **TRUE** nebo **FALSE**.

Pokud hodnotu **TRUE**, počet vláken, která se používají k provádění paralelních oblastí může být upraveno pomocí běhové prostředí co nejlépe využívat základní systémové prostředky.  Pokud hodnotu **FALSE**, dynamické přizpůsobení je zakázaná. Výchozí stav je definován implementací.

Příklad:

```
setenv OMP_DYNAMIC TRUE
```

## <a name="cross-references"></a>Křížové odkazy:

- Další informace o paralelních oblastí najdete v tématu [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.

- **omp_set_dynamic –** funkce naleznete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.