---
title: 3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f480a75efff737356c1477593e182537ae73a8c8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690218"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce
Tyto funkce jsou prostředkem vydání vlastnictví zámek. Formát vypadá takto:  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Argument pro každou z těchto funkcí musí odkazovat na proměnnou inicializovaného zámku vlastníkem vláken provádění funkce. Chování není definována, pokud vlákno není vlastníkem této zámku.  
  
 Pro jednoduché zámku `omp_unset_lock` funkce uvolní vlákno provádění funkce z vlastnictví zámku.  
  
 Na nestable Zámek `omp_unset_nest_lock` funkce sníží počet vnoření a verze vláken provádění funkce z vlastnictví zámku, pokud je výsledný počet nula.