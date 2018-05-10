---
title: Příklady A.25 copyprivate Data atribut klauzule | Microsoft Docs
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
ms.openlocfilehash: c92d9ce6f22c2d53a2e65d7b67c22e4f080f162c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25   Příklady klauzule datového atributu copyprivate
**Příklad 1:** `copyprivate` – klauzule ([části 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stránce 32) slouží k vysílání hodnoty získané jedno vlákno přímo na všechny instance soukromé proměnné v jiná vlákna.  
  
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
  
 Pokud rutiny *init* je volána z sériové oblasti, nemá vliv své chování přítomnost direktivy. Po zavolání *get_values* rutiny provedl jedním vláknem, žádný přístup z více vláken opustí konstruktu dokud privátní objekty určené, které *a*, *b*, *x*, a *y* v všechna vlákna stát definovali s hodnotami pro čtení.  
  
 **Příklad 2:** na rozdíl od předchozí příklad předpokládejme čtení musí provést určitý vlákno, například hlavní vlákno. V takovém případě `copyprivate` klauzuli nelze použít přímo udělat vysílání, ale může sloužit k poskytování přístupu k dočasné sdíleném objektu.  
  
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
  
 **Příklad 3:** Předpokládejme, že počet objektů zámku potřebné v rámci paralelní oblasti, které nelze snadno určit před jeho zadávání. `copyprivate` Klauzuli lze použít k poskytování přístupu k sdílený zámek objekty, které jsou přiděleny v rámci této paralelní oblasti.  
  
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