---
title: omezit | Microsoft Docs
ms.custom: 
ms.date: 02/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec1a54e9c4f235de4aad796586cd7be3e7ee592e
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2018
---
# <a name="restrict"></a>restrict

**Microsoft Specific**

Při použití funkce deklarace nebo definice, která vrátí hodnotu typu ukazatele `restrict` říká kompilátoru, funkce vrátí objekt, který není *alias*, tedy odkazují jiné ukazatele. To umožňuje kompilátoru provést další optimalizace.

## <a name="syntax"></a>Syntaxe

> **__declspec(restrict)** *pointer_return_type* *function*();  
  
## <a name="remarks"></a>Poznámky

Kompilátor rozšíří `__declspec(restrict)`. Například CRT `malloc` funkce má `__declspec(restrict)` dekorace a proto kompilátor předpokládá, že ukazatele inicializována tak, aby umístění v paměti podle `malloc` nejsou také alias podle dříve existující ukazatele.

Kompilátor nekontroluje, že vrácený ukazatel není ve skutečnosti alias. Odpovědností vývojáře je zajistit, aby programátor nevytvořil alias na ukazatel, který je označen modifikátorem `restrict __declspec`.  
  
Podobnou sémantiku na proměnné, najdete v části [__restrict](../cpp/extension-restrict.md).
 
Další poznámky, která platí pro aliasy v rámci funkce, najdete v části [__declspec(noalias)](../cpp/noalias.md).
  
Informace o **omezit** – klíčové slovo, který je součástí C++ AMP, najdete v části [omezení (C++ AMP)](../cpp/restrict-cpp-amp.md).  
 
## <a name="example"></a>Příklad  

Následující příklad ukazuje použití `__declspec(restrict)`.

Když `__declspec(restrict)` se použije pro funkce, vrátí ukazatele, tato hodnota informuje kompilátor paměti ukazuje návratová hodnota není alias. V tomto příkladu následující ukazatele `mempool` a `memptr` jsou globální, takže kompilátor nemůže být se, že paměť použijí pro referenci není alias. Však se používají v rámci `ma` a jeho volající `init` způsobem, který vrátí paměti, která není v opačném případě odkazuje programu, takže `__decslpec(restrict)` pomáhají okně Optimalizace. Toto je podobná jak hlavičky CRT uspořádání přidělení funkce, jako `malloc` pomocí `__declspec(restrict)` k označení, že vždy vracet paměti, která nejde používat aliasy ukazateli existující.

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)  
[__declspec](../cpp/declspec.md)  
[__declspec(noalias)](../cpp/noalias.md)  
