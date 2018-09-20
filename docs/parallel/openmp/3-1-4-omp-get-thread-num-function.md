---
title: 3.1.4 omp_get_thread_num – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a21a682c051daffde16b3d5cfc63fd2d679c4de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444915"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num – funkce

`omp_get_thread_num` Funkce vrací číslo vlákna, v rámci jeho týmu vlákna provádění funkce. Vlákno číslo leží mezi 0 a **omp_get_num_threads()**-1 (včetně). Hlavní vlákno týmu je vlákno 0.

Formát je následujícím způsobem:

```
#include <omp.h>
int omp_get_thread_num(void);
```

Pokud je volána ze sériového portu oblasti `omp_get_thread_num` vrátí hodnotu 0. Je-li volat v rámci vnořených paralelní oblasti, která je serializovaná, tato funkce vrátí 0.

## <a name="cross-references"></a>Křížové odkazy:

- `omp_get_num_threads` Funkce, najdete v článku [části 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stránce 37.