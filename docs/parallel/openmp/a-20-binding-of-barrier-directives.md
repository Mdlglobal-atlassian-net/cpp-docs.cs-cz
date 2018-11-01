---
title: A.20   Vazby direktiv barrier
ms.date: 11/04/2016
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
ms.openlocfilehash: cf6f20a8539c47ca529af93e65f3a5fe244228d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652943"
---
# <a name="a20---binding-of-barrier-directives"></a>A.20   Vazby direktiv barrier

Vazby direktiv pravidla pro volání **bariéry** směrnice vytvořit vazbu na nejbližší uzavírající `parallel` – direktiva. Další informace o vazby direktiv, naleznete v tématu [části 2.8](../../parallel/openmp/2-8-directive-binding.md) na stránce 32.

V následujícím příkladu volání z *hlavní* k *sub2* je kompatibilní s protože **bariéry** (v *sub3*) vytvoří vazbu paralelní oblasti v *sub2*. Volání z *hlavní* k *sub1* je kompatibilní s protože **bariéry** váže k paralelní oblastí v podprogram *sub2*.  Volání z *hlavní* k *sub3* vyhovuje protože **bariéry** nemá vazbu v jakémkoli paralelní oblasti a je ignorován. Všimněte si také, **bariéry** synchronizuje pouze týmu vlákna v nadřazeném paralelní oblasti a ne všechna vlákna vytvořená v *sub1*.

```
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```