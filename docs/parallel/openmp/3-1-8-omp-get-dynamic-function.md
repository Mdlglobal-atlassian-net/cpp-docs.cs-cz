---
title: 3.1.8 omp_get_dynamic – funkce
ms.date: 11/04/2016
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
ms.openlocfilehash: d9476894e5aff4cc7bb9c67fbbeb14d185b65f5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566423"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic – funkce

**Omp_get_dynamic –** funkce vrací nenulovou hodnotu, pokud je povolené dynamické přizpůsobení vlákna a v opačném případě vrátí 0. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_get_dynamic(void);
```

Implementace neimplementuje dynamické úpravy počtu vláken, tato funkce vždy vrátí hodnotu 0.

## <a name="cross-references"></a>Křížové odkazy:

- Popis nastavení dynamické vlákno, naleznete v tématu [části 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stránce 39.