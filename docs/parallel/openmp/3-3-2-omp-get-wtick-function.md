---
title: 3.3.2 omp_get_wtick – funkce
ms.date: 11/04/2016
ms.assetid: 1ad08500-bcb0-40d9-a81f-f131819006c9
ms.openlocfilehash: af1e5cf8ef40621342a5162f90cf8c883a59c6a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617955"
---
# <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick – funkce

`omp_get_wtick` Funkce vrátí hodnotu dvojité přesnosti s plovoucí desetinnou čárkou bodu rovna počtu sekund mezi po sobě jdoucích taktů. Formát je následujícím způsobem:

```
#include <omp.h>
double omp_get_wtick(void);
```