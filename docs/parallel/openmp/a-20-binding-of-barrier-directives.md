---
title: A.20 vazby direktiv barrier | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 628920caa6a122230f42394cc757e3abdb1874cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381306"
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