---
title: omp_get_wtime | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_wtime
dev_langs:
- C++
helpviewer_keywords:
- omp_get_wtime OpenMP function
ms.assetid: c8dee105-ec1b-42e5-a6e3-edeedcf9854c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f2d02bf5b8de0094a18d456a569b24fed2e03b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391758"
---
# <a name="ompgetwtime"></a>omp_get_wtime

Vrátí že hodnotu v sekundách času uplynulo v určitém okamžiku.

## <a name="syntax"></a>Syntaxe

```
double omp_get_wtime( );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí že hodnotu v sekundách času uplynulo z některé libovolného, ale konzistentního bodu.

## <a name="remarks"></a>Poznámky

Tento bod zůstane konzistentní při provádění programu, umožňující další porovnání.

Další informace najdete v tématu [3.3.1 omp_get_wtime – funkce](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

## <a name="example"></a>Příklad

```
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="see-also"></a>Viz také

[Funkce](../../../parallel/openmp/reference/openmp-functions.md)