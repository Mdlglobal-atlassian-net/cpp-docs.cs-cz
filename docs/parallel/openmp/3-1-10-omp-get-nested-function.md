---
title: 3.1.10 omp_get_nested – funkce
ms.date: 11/04/2016
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
ms.openlocfilehash: a4db1e21f344f5cc58e2027b0816f9c8fb40b3bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519915"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested – funkce

`omp_get_nested` Funkce vrátí nenulovou hodnotu, pokud je povolené vnořené paralelismu a 0, pokud je zakázaná. Další informace o vnořených paralelismu najdete v části 3.1.9 na stránce 40. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_get_nested(void);
```

Implementace neimplementuje vnořené paralelismu, tato funkce vždy vrátí hodnotu 0.