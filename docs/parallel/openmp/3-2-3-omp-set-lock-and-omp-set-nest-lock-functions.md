---
title: "3.2.3 omp_set_lock a omp_set_nest_lock – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5f78307023091b2e9d17ca3ff8fa2d3214c458cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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