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
ms.openlocfilehash: 97cf6ccad0a3b30c0abfa0076ea9c6a30b205d67
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065197"
---
# <a name="openmp-data-types"></a>OpenMP – datové typy

Obsahuje odkazy na datové typy používané v rozhraní API OpenMP.

Implementace jazyka Visual C++, OpenMP standard zahrnuje následující datové typy.

|Datový typ|Popis|
|---------|-----------|
|[omp_lock_t](#omp-lock-t)|Typ, který obsahuje stav zámku, určuje, zda je k dispozici zámek nebo pokud vlákno vlastníkem zámku.|
|[omp_nest_lock_t](#omp-nest-lock-t)|Typ, který obsahuje jeden z následujících částí informace o zámku: zda zámek je k dispozici a identitu vlákna, která vlastní zámek a počet vnoření.|

## <a name="omp-lock-t"></a>omp_lock_t.

Typ, který obsahuje stav zámku, určuje, zda je k dispozici zámek nebo pokud vlákno vlastníkem zámku.

Tyto funkce použijte `omp_lock_t`:

- [omp_init_lock](openmp-functions.md#omp-init-lock)
- [omp_destroy_lock](openmp-functions.md#omp-destroy-lock)
- [omp_set_lock](openmp-functions.md#omp-set-lock)
- [omp_unset_lock](openmp-functions.md#omp-unset-lock)
- [omp_test_lock](openmp-functions.md#omp-test-lock)

Další informace najdete v tématu [3.2 funkce zamykání](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Příklad

Zobrazit [omp_init_lock](openmp-functions.md#omp-init-lock) pro příklad použití `omp_lock_t`.

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t.

Typ, který obsahuje následující časti informace o zámku: zda zámek je k dispozici a identitu vlákna, která vlastní zámek a počet vnoření.

Tyto funkce použijte `omp_nest_lock_t`:

- [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock)
- [omp_destroy_nest_lock](openmp-functions.md#omp-destroy-nest-lock)
- [omp_set_nest_lock](openmp-functions.md#omp-set-nest-lock)
- [omp_unset_nest_lock](openmp-functions.md#omp-unset-nest-lock)
- [omp_test_nest_lock](openmp-functions.md#omp-test-nest-lock)

Další informace najdete v tématu [3.2 funkce zamykání](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Příklad

Zobrazit [omp_init_nest_lock –](openmp-functions.md#omp-init-nest-lock) pro příklad použití `omp_nest_lock_t`.
