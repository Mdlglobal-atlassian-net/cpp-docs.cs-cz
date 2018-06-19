---
title: noalias | Microsoft Docs
ms.custom: ''
ms.date: 02/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noalias_cpp
dev_langs:
- C++
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cbb5c1b4162f3326aade092c7e20ca42a825d13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420116"
---
# <a name="noalias"></a>noalias

**Konkrétní Microsoft**

`noalias` znamená, že volání funkce upravit nebo odkazovat viditelné globální stav a pouze upraví paměti ukazuje *přímo* parametry ukazatele (první úrovně indirections).

Pokud je funkce označena jako `noalias`, optimalizátor může předpokládat, že kromě parametrů samotných jsou odkazována pouze nepřímá odkazování parametrů ukazatele nebo jsou upraveny uvnitř funkce. Stav globální viditelnosti je sada všech dat, která nejsou definována nebo odkazována mimo rozsah kompilace a jejich adresa není přebrána. Kompilace obor je všechny zdrojové soubory ([/ltgc (vytváření kódu v době propojování)](../build/reference/ltcg-link-time-code-generation.md) sestavení) nebo jeden zdrojový soubor (jinou hodnotu než **/ltgc** sestavení).

`noalias` Poznámky platí jenom v rámci obsah opatřen poznámkami funkce. Označení funkce jako `__declspec(noalias)` nemá vliv aliasy ukazatele vráceným funkcí.

Další poznámky, která může ovlivnit aliasy, najdete v části [__declspec(restrict)](../cpp/restrict.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `__declspec(noalias)`.

Když funkce `multiply` , přistupuje paměti je poznámkou `__declspec(noalias)`, říká kompilátoru tuto funkci nelze změnit stav globální kromě prostřednictvím ukazatele ve svém seznamu parametr.

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
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

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)  
[Klíčová slova](../cpp/keywords-cpp.md)  
[__declspec(restrict)](../cpp/restrict.md)  
