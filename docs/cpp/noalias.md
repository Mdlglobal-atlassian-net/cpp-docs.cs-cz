---
title: noalias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: noalias_cpp
dev_langs: C++
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1b70c5e41b3380de241939249f51449ba65406c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="noalias"></a>noalias

**Konkrétní Microsoft**

`noalias`znamená, že volání funkce upravit nebo odkazovat viditelné globální stav a pouze upraví paměti ukazuje *přímo* parametry ukazatele (první úrovně indirections).

Pokud je funkce označena jako `noalias`, optimalizátor může předpokládat, že kromě parametrů samotných jsou odkazována pouze nepřímá odkazování parametrů ukazatele nebo jsou upraveny uvnitř funkce. Stav globální viditelnosti je sada všech dat, která nejsou definována nebo odkazována mimo rozsah kompilace a jejich adresa není přebrána. Kompilace obor je všechny zdrojové soubory ([/ltgc (vytváření kódu v době propojování)](../build/reference/ltcg-link-time-code-generation.md) sestavení) nebo jeden zdrojový soubor (jinou hodnotu než**/ltgc** sestavení).

## <a name="example"></a>Příklad

Následující příklad ukazuje použití `__declspec(restrict)` a `__declspec(noalias)`. Za normálních okolností paměti vrácená z `malloc` je `restrict` vzhledem k tomu, že jsou správně dekorované CRT hlavičky.

Ale v tomto příkladu následující ukazatele `mempool` a `memptr` jsou globální, takže kompilátor má záruka, že velikost paměti není v souladu aliasy. Upravení funkcí, které vracejí ukazatele s `__declspec(restrict)`, informuje kompilátor, že paměť, na níž je odkazováno návratovou hodnotou, není aliasována.

Upravení funkce, která v tomto příkladu přistupuje do paměti pomocí `__declspec(noalias)`, sděluje kompilátoru, že se tato funkce neovlivňuje s globálním stavem, s výjimkou ukazatelů jejího seznamu parametrů.

```C
// declspec_noalias.c
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