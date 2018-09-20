---
title: firstprivate | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d070b8de3cf0382447c3b8e756140892dcd85edc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387117"
---
# <a name="firstprivate"></a>firstprivate

Určuje, že každé vlákno má svoji vlastní instanci proměnné. proto, že proměnné by měl inicializovat pomocí hodnoty proměnné, protože existuje před paralelní konstrukce.

## <a name="syntax"></a>Syntaxe

```
firstprivate(var)
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`var`|U instancí v každé vlákno a které proměnné se inicializuje s hodnotu proměnné, protože existuje před paralelní konstrukce. Pokud je zadán více než jednu proměnnou, oddělte názvy proměnných čárkou.|

## <a name="remarks"></a>Poznámky

## <a name="remarks"></a>Poznámky

`firstprivate` platí pro následující direktivy:

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)

- [single](../../../parallel/openmp/reference/single.md)

Další informace najdete v tématu [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).

## <a name="example"></a>Příklad

Příklad použití `firstprivate`, podívejte se na příklad v [privátní](../../../parallel/openmp/reference/private-openmp.md).

## <a name="see-also"></a>Viz také

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)