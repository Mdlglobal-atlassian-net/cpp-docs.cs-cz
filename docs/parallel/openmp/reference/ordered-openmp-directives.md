---
title: seřazené (direktivy OpenMP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- ordered
dev_langs:
- C++
helpviewer_keywords:
- ordered OpenMP directive
ms.assetid: e1aa703e-d07d-4f6a-9b2a-f4f25203d850
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d999503a8f5802056c32329bf68e62383cbd53f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420852"
---
# <a name="ordered-openmp-directives"></a>ordered (direktivy OpenMP)

Určuje, že kód v rámci paralelizovaná smyčka by měl být spuštěn jako sekvenční smyčka.

## <a name="syntax"></a>Syntaxe

```
#pragma omp ordered
   structured-block
```

## <a name="remarks"></a>Poznámky

**Seřazené** direktiva musí být v rámci dynamický rozsah [pro](../../../parallel/openmp/reference/for-openmp.md) nebo **paralelní pro** vytvořit pomocí **seřazené** klauzuli.

**Seřazené** podporuje bez klauzule OpenMP – direktiva.

Další informace najdete v tématu [2.6.6 ordered – konstrukce](../../../parallel/openmp/2-6-6-ordered-construct.md).

## <a name="example"></a>Příklad

```
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="see-also"></a>Viz také

[Direktivy](../../../parallel/openmp/reference/openmp-directives.md)