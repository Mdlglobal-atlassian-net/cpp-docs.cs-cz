---
title: 4.4 OMP_NESTED | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1083269f31ebc710da24430635ff8381e3f2147a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419513"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED` Proměnnou prostředí povolí nebo zakáže vnořené paralelismu, pokud je povoleno nebo zakázáno voláním vnořené paralelismu `o` **mp_set_nested** rutina knihovny. Pokud nastavena na **TRUE**, vnořené paralelismu je povolené; Pokud je nastavena na **FALSE**vnořené paralelismu je zakázaná. Výchozí hodnota je **FALSE**.

Příklad:

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>Křížový odkaz:

- `omp_set_nested` Funkce, najdete v článku [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40.