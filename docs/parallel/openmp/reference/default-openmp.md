---
title: Výchozí (OpenMP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- default
dev_langs:
- C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea32f473d96c8f48c6628d8f71212269bd6d345
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392606"
---
# <a name="default-openmp"></a>default (OpenMP)

Určuje chování bez ohledu na obor proměnné v paralelní oblasti.

## <a name="syntax"></a>Syntaxe

```
default(shared | none)
```

## <a name="remarks"></a>Poznámky

`shared`, což je v platnosti Pokud `default` není zadána klauzule, znamená to, že všechny proměnné v paralelní oblasti zpracovávány jako by to byly zadány s [sdílené](../../../parallel/openmp/reference/shared-openmp.md) klauzule. `none` znamená, že všechny proměnné, používat v paralelní oblasti, která nejsou obor [privátní](../../../parallel/openmp/reference/private-openmp.md), [sdílené](../../../parallel/openmp/reference/shared-openmp.md), [snížení](../../../parallel/openmp/reference/reduction.md), [firstprivate](../../../parallel/openmp/reference/firstprivate.md), nebo [lastprivate](../../../parallel/openmp/reference/lastprivate.md) klauzule způsobí chybu kompilátoru.

`default` platí pro následující direktivy:

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)

Další informace najdete v tématu [2.7.2.5 výchozí](../../../parallel/openmp/2-7-2-5-default.md).

## <a name="example"></a>Příklad

Zobrazit [privátní](../../../parallel/openmp/reference/private-openmp.md) pro příklad použití `default`.

## <a name="see-also"></a>Viz také

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)