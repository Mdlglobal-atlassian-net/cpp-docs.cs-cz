---
title: A.25 příklady klauzule datového atributu copyprivate | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95d68c445c1c20e97725d869061027a9712c2462
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413630"
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25   Příklady klauzule datového atributu copyprivate

**Příklad 1:** `copyprivate` – klauzule ([části 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stránce 32) slouží k vysílání hodnoty získané jedno vlákno přímo na všechny instance soukromé proměnné v jiných vláken.

```
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

Pokud rutiny *init* nazývá ze sériového portu oblasti své chování nemá vliv na přítomnost direktivy. Po zavolání *get_values* rutiny provedl jedním vláknem, žádný přístup z více vláken opustí konstruktu dokud privátní objekty určené, které *a*, *b*, *x*, a *y* v všechna vlákna stát definovali s hodnotami pro čtení.

**Příklad 2:** na rozdíl od předchozího příkladu předpokládejme, že čtení se musí provádět konkrétní vlákno, Dejme tomu, že hlavní vlákno. V takovém případě `copyprivate` klauzuli nelze použít přímo provedete vysílání, ale je možné poskytnout přístup ke sdílené dočasný objekt.

```
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**Příklad 3:** Předpokládejme, že počet objektů zámek vyžaduje v rámci paralelní oblasti, které nelze snadno určit ještě než ho přidáte. `copyprivate` Klauzuli lze použít pro poskytnutí přístupu k sdílený zámek objekty, které jsou přiděleny v rámci dané paralelní oblasti.

```
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```