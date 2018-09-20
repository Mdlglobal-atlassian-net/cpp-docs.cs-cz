---
title: omp_unset_lock | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_lock OpenMP function
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe6d24c6d4fe6cd1df1eea6f0e575ff5c7947c56
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417043"
---
# <a name="ompunsetlock"></a>omp_unset_lock

Uvolní zámek.

## <a name="syntax"></a>Syntaxe

```
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) , který byl inicializován s [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)vlastněné uživatelem vlákna a provádění ve funkci.

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

## <a name="example"></a>Příklad

Zobrazit [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) pro příklad použití `omp_unset_lock`.

## <a name="see-also"></a>Viz také

[Funkce](../../../parallel/openmp/reference/openmp-functions.md)