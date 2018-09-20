---
title: omp_unset_nest_lock – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_nest_lock OpenMP function
ms.assetid: 1721d061-3f9c-45d7-b479-a665cd0a121d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03ea941e793f8c3a9f40e0495442deb71b2ffa93
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402717"
---
# <a name="ompunsetnestlock"></a>omp_unset_nest_lock

Uvolní, vnořitelných zámek.

## <a name="syntax"></a>Syntaxe

```
void omp_unset_nest_lock( 
   omp_nest_lock_t *lock 
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Proměnné typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) , který byl inicializován s [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md)vlastněné uživatelem vlákna a provádění ve funkci.

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

## <a name="example"></a>Příklad

Zobrazit [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md) pro příklad použití `omp_unset_nest_lock`.

## <a name="see-also"></a>Viz také

[Funkce](../../../parallel/openmp/reference/openmp-functions.md)