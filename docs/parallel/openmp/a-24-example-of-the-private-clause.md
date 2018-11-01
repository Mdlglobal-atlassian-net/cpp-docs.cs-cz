---
title: A.24   Příklady použití klauzule private
ms.date: 11/04/2016
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
ms.openlocfilehash: facf5b953b26d284f6bfed4f35a9162f6d2bf212
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552955"
---
# <a name="a24---example-of-the-private-clause"></a>A.24   Příklady použití klauzule private

`private` – Klauzule ([části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25) paralelní oblasti je platná pouze pro lexikální rozsah oblast, nikoli pro dynamický rozsah oblasti.  Proto v příkladu, který následuje, všechny používá proměnnou *a* v rámci `for` smyčky v rutině *f* odkazuje privátní kopie *a*, při použití v rutiny *g* odkazuje na globální *a*.

```
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```