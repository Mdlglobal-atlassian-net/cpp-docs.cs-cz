---
title: omp_get_dynamic – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2b5a285ef019cd1752b60065f7040d9a937ce38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389886"
---
# <a name="ompgetdynamic"></a>omp_get_dynamic

Vrátí hodnotu určující, pokud je možné upravit počet vláken v následných paralelní oblasti podle času spuštění.

## <a name="syntax"></a>Syntaxe

```
int omp_get_dynamic();
```

## <a name="return-value"></a>Návratová hodnota

Pokud je povolené nenulovou hodnotu, dynamické úpravy vláken.

## <a name="remarks"></a>Poznámky

Dynamické přizpůsobení vláken není zadán s [omp_set_dynamic –](../../../parallel/openmp/reference/omp-set-dynamic.md) a [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md).

Další informace najdete v tématu [3.1.7 omp_set_dynamic – funkce](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

## <a name="example"></a>Příklad

Zobrazit [omp_set_dynamic –](../../../parallel/openmp/reference/omp-set-dynamic.md) pro příklad použití `omp_get_dynamic`.

## <a name="see-also"></a>Viz také

[Funkce](../../../parallel/openmp/reference/openmp-functions.md)