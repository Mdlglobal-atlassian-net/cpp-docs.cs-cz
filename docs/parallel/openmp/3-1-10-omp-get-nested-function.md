---
title: 3.1.10 omp_get_nested – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d019dd757080bbc87ff7aaab1a8745b2a3156b39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392278"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested – funkce

`omp_get_nested` Funkce vrátí nenulovou hodnotu, pokud je povolené vnořené paralelismu a 0, pokud je zakázaná. Další informace o vnořených paralelismu najdete v části 3.1.9 na stránce 40. Formát je následujícím způsobem:

```
#include <omp.h>
int omp_get_nested(void);
```

Implementace neimplementuje vnořené paralelismu, tato funkce vždy vrátí hodnotu 0.