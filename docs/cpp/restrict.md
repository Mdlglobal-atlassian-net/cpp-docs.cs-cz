---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: 40c1c05ca72f639829f2d3658497b0e9f3199640
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431743"
---
# <a name="restrict"></a>restrict

**Specifické pro Microsoft**

Při použití u deklarace funkce nebo definice, která vrací typ ukazatele, **omezit** sděluje kompilátoru, že funkce vrátí objekt, který není *alias*, to znamená, odkazuje jiný ukazatele. To umožňuje kompilátoru provést další optimalizace.

## <a name="syntax"></a>Syntaxe

> **__declspec(restrict)** *pointer_return_type* *function*();

## <a name="remarks"></a>Poznámky

Kompilátor šíří **__declspec(restrict)**. Například CRT `malloc` má funkce **__declspec(restrict)** dekorace a proto kompilátor předpokládá, že ukazatele inicializované do umístění v paměti podle `malloc` nejsou také alias podle dříve existující ukazatele.

Kompilátor nekontroluje, vrácený ukazatel není ve skutečnosti vytvořen alias. Je odpovědností vývojáře zajistit, aby programátor nevytvořil alias ukazatel označené **omezit __declspec** modifikátor.

Podobné sémantiky proměnných naleznete v tématu [kvalifikátor __restrict](../cpp/extension-restrict.md).

Jinou anotaci, která se vztahuje pouze na aliasing v rámci funkce, najdete v části [__declspec(noalias)](../cpp/noalias.md).

Informace o tom, **omezit** – klíčové slovo, který je součástí C++ AMP, naleznete v tématu [omezení (C++ AMP)](../cpp/restrict-cpp-amp.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje použití **__declspec(restrict)**.

Když **__declspec(restrict)** se použije na funkci, vrátí ukazatel, to kompilátoru říká, že paměť odkazovanou na návratovou hodnotou není alias. V tomto příkladu ukazatelů `mempool` a `memptr` jsou globální, proto kompilátor nemůže být, že odkazují na paměť není alias. Nicméně se používají v rámci `ma` a jeho volající `init` způsobem, který vrátí paměti, které jinak neodkazuje na program, takže **__decslpec(restrict)** slouží ke snadnější Optimalizátor. Podobá se to jak záhlaví CRT uspořádání přidělení funkce, jako `malloc` pomocí **__declspec(restrict)** k označení, že vždy vrátí paměť řádně nelze používat aliasy pomocí existující ukazatelů.

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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec(noalias)](../cpp/noalias.md)
