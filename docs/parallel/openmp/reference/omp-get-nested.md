---
title: omp_get_nested – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20a7378ba7e7f6dcec55cfe265dd0873bdc1fd38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371950"
---
# <a name="ompgetnested"></a>omp_get_nested

Vrátí hodnotu, která označuje, zda je povoleno vnořené paralelismu.

## <a name="syntax"></a>Syntaxe

```
int omp_get_nested( );
```

## <a name="return-value"></a>Návratová hodnota

Pokud je povolené nenulovou hodnotu, vnořené paralelismu.

## <a name="remarks"></a>Poznámky

Vnořené paralelismu zadán s parametrem [omp_set_nested –](../../../parallel/openmp/reference/omp-set-nested.md) a [OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md).

Další informace najdete v tématu [3.1.10 omp_get_nested – funkce](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

## <a name="example"></a>Příklad

Zobrazit [omp_set_nested –](../../../parallel/openmp/reference/omp-set-nested.md) pro příklad použití `omp_get_nested`.

## <a name="see-also"></a>Viz také

[Funkce](../../../parallel/openmp/reference/openmp-functions.md)