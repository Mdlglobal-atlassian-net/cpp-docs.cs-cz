---
title: noalias | Dokumentace Microsoftu
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
ms.openlocfilehash: a10acd24fed4dadb6bd33b66c895dc94f7215cb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102799"
---
# <a name="noalias"></a>noalias

**Specifické pro Microsoft**

**noalias** znamená, že volání funkce neupravuje nebo neodkazuje na globální stav a pouze upravuje paměť odkazovanou na *přímo* parametry ukazatele (nepřímé odkazy na první úrovni).

Pokud je funkce označena jako **noalias**, optimalizátor může předpokládat, že kromě parametrů samotných pouze nepřímá odkazování parametrů ukazatele jsou odkazovaná nebo upraveny uvnitř funkce. Stav globální viditelnosti je sada všech dat, která nejsou definována nebo odkazována mimo rozsah kompilace a jejich adresa není přebrána. Oborem kompilace jsou všechny zdrojové soubory ([parametru/LTCG (generování kódu při propojování odkaz)](../build/reference/ltcg-link-time-code-generation.md) sestavení) nebo jeden zdrojový soubor (jinou hodnotu než**parametru/LTCG** sestavení).

**Noalias** poznámky platí jenom v těle funkce s poznámkami. Označení funkci tak, aby **__declspec(noalias)** nemá vliv na aliasing ukazatele vrácené funkcí.

Další poznámky, které můžou ovlivnit aliasing, naleznete v tématu [__declspec(restrict)](../cpp/restrict.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje použití **__declspec(noalias)**.

Když funkce `multiply` , je opatřen přístupy do paměti **__declspec(noalias)**, sděluje kompilátoru, že tato funkce neupravuje globálním stavem, s výjimkou ukazatelů jejího seznamu parametrů.

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

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[__declspec(restrict)](../cpp/restrict.md)
