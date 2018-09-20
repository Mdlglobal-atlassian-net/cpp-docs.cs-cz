---
title: Atomic | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- atomic
dev_langs:
- C++
helpviewer_keywords:
- atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c845f6147280e7248db7899a182eed8d71fc34f5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442692"
---
# <a name="atomic"></a>atomic

Určuje, že umístění v paměti, která bude aktualizována atomicky.

## <a name="syntax"></a>Syntaxe

```
#pragma omp atomic
   expression
```

#### <a name="parameters"></a>Parametry

*Výraz*<br/>
Příkazu, který obsahuje hodnoty lvalue, umístění v paměti, které chcete chránit proti více zápisy. Další informace o platný výraz formuláře naleznete v tématu Specifikace OpenMP.

## <a name="remarks"></a>Poznámky

`atomic` Podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [vytvořit 2.6.4 atomic](../../../parallel/openmp/2-6-4-atomic-construct.md).

## <a name="example"></a>Příklad

```
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="see-also"></a>Viz také

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)