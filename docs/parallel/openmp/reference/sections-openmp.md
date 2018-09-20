---
title: oddíly (OpenMP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- section
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- sections OpenMP directive
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32dab6784e4265432f596b585e098f6a77687117
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421541"
---
# <a name="sections-openmp"></a>sections (OpenMP)

Identifikuje části kódu k rozdělení mezi všemi vlákny.

## <a name="syntax"></a>Syntaxe

```
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   } 
}
```

## <a name="arguments"></a>Arguments

*Klauzule*<br/>
(Volitelné) Nula nebo více klauzulí. Naleznete v části poznámky pro seznam klauzule podporované službou **oddíly**.

## <a name="remarks"></a>Poznámky

**Oddíly** směrnice může obsahovat nula nebo více **části** direktivy.

**Oddíly** podporuje následující klauzule OpenMP – direktiva:

- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)

- [lastprivate](../../../parallel/openmp/reference/lastprivate.md)

- [nowait](../../../parallel/openmp/reference/nowait.md)

- [private](../../../parallel/openmp/reference/private-openmp.md)

- [reduction](../../../parallel/openmp/reference/reduction.md)

Pokud **paralelní** je také zadána, `clause` může být jakékoli klauzule přijal **paralelní** nebo **oddíly** direktivy, s výjimkou `nowait`.

Další informace najdete v tématu [2.4.2 sections – konstrukce](../../../parallel/openmp/2-4-2-sections-construct.md).

## <a name="example"></a>Příklad

```
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="see-also"></a>Viz také

[Direktivy](../../../parallel/openmp/reference/openmp-directives.md)