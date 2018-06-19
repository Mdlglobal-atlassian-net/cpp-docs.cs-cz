---
title: 3.2.3 omp_set_lock a omp_set_nest_lock – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba24e923051eb887db2a81c1d9765d31a4ef7b24
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689711"
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock a omp_set_nest_lock – funkce
Každá z těchto funkcí blokuje vlákno provádění funkce, dokud zadaný zámek je k dispozici a poté nastaví zámek. Jednoduché zámek je k dispozici, pokud je odemčený. Nestable zámek je k dispozici, pokud je odemčený, nebo pokud je již vlastněn vlákno provádění funkce. Formát vypadá takto:  
  
```  
#include <omp.h>  
void omp_set_lock(omp_lock_t *lock);  
void omp_set_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Na jednoduchý zámek argument `omp_set_lock` funkce musí odkazovat na proměnnou inicializovaného zámku. Vlákno provádění funkce uděleno vlastnictví zámku.  
  
 Na nestable zámek argument `omp_set_nest_lock` funkce musí odkazovat na proměnnou inicializovaného zámku. Se zvýší počet vnoření a vlákno je povolen, nebo uchovává vlastnictví zámku.