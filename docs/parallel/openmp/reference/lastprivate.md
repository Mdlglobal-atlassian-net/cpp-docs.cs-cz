---
title: lastprivate | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7124e51b604a55d049be13d3bbcccc4e5810ca67
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412831"
---
# <a name="lastprivate"></a>lastprivate

Určuje, že verze nadřazeného objektu context proměnné je nastavena na soukromou verzi podle toho, která vlákno spustí poslední iterace (konstrukci smyčky for-loop) nebo poslední část (#pragma oddílů).

## <a name="syntax"></a>Syntaxe

```
lastprivate(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Proměnné, která je nastavena na soukromou verzi podle toho, která vlákna spustí poslední iterace (konstrukci smyčky for-loop) nebo poslední část (#pragma oddílů).

## <a name="remarks"></a>Poznámky

`lastprivate` platí pro následující direktivy:

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)

Další informace najdete v tématu [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).

## <a name="example"></a>Příklad

Zobrazit [plán](../../../parallel/openmp/reference/schedule.md) pro příklad použití `lastprivate` klauzuli.

## <a name="see-also"></a>Viz také

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)