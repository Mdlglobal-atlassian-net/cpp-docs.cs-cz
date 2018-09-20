---
title: 3.1.6 omp_in_parallel – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ba6c35d42f8497869894bd5ec95b83f0c8793f1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404615"
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel – funkce

**Omp_in_parallel** funkce vrátí nenulovou hodnotu, pokud je volána v rámci dynamický rozsah paralelní oblasti paralelně prováděných; v opačném případě vrátí hodnotu 0. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_in_parallel(void);
```

Tato funkce vrátí nenulovou hodnotu při volání z v rámci oblasti spouští paralelně, včetně vnořených oblastí, které se serializují.