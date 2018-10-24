---
title: OpenMP – datové typy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP data types
- omp_lock_t
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- OpenMP data types
- omp_lock_t OpenMP data type
- omp_nest_lock_t OpenMP data type
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 254dffebc258867088f738b10a11bf48d31bd0a4
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990060"
---
# <a name="openmp-data-types"></a>OpenMP – datové typy

Obsahuje odkazy na datové typy používané v rozhraní API OpenMP.

Implementace jazyka Visual C++, OpenMP standard zahrnuje následující datové typy.

Datový typ                           | Popis
----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[omp_lock_t](#omp-lock-t)           | Typ, který obsahuje stav zámku, určuje, zda je k dispozici zámek nebo pokud vlákno vlastníkem zámku.
[omp_nest_lock_t](#omp-nest-lock-t) | Typ, který obsahuje jeden z následujících částí informace o zámku: zda zámek je k dispozici a identitu vlákna, která vlastní zámek a počet vnoření.

## <a name="omp-lock-t"></a>omp_lock_t.

Typ, který obsahuje stav zámku, určuje, zda je k dispozici zámek nebo pokud vlákno vlastníkem zámku.

Tyto funkce použijte `omp_lock_t`:

- [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)
- [omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)
- [omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)
- [omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)
- [omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)

Další informace najdete v tématu [3.2 funkce zamykání](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Příklad

Zobrazit [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) pro příklad použití `omp_lock_t`.

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t.

Typ, který obsahuje následující časti informace o zámku: zda zámek je k dispozici a identitu vlákna, která vlastní zámek a počet vnoření.

Tyto funkce použijte `omp_nest_lock_t`:

- [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)
- [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)
- [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)
- [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)
- [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)

Další informace najdete v tématu [3.2 funkce zamykání](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Příklad

Zobrazit [omp_init_nest_lock –](../../../parallel/openmp/reference/omp-init-nest-lock.md) pro příklad použití `omp_nest_lock_t`.
