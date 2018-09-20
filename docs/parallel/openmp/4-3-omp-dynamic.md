---
title: 4.3 OMP_DYNAMIC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c15fa9d8c9d86b736bfc577a3b17e9809ec9baaf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439195"
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