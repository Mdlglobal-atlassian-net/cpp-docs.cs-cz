---
title: "3.2.5 omp_test_lock a omp_test_nest_lock – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fa340ce56d0e669a40b131a4cb3efbe18fc3c430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock a omp_test_nest_lock – funkce
Tyto funkce k pokusu nastavit zámek ale neblokují provádění vlákna. Formát vypadá takto:  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Argument musí odkazovat na proměnnou inicializovaného zámku. Tyto funkce k pokusu nastavit zámek stejným způsobem jako `omp_set_lock` a `omp_set_nest_lock`kromě toho, že nebrání provádění vlákna.  
  
 Pro jednoduché zámku `omp_test_lock` funkce vrátí nenulovou hodnotu, pokud se úspěšně nastavila zámek; jinak vrátí hodnotu nula.  
  
 Na nestable Zámek `omp_test_nest_lock` funkce vrací nový počet vnoření, pokud se úspěšně nastavila zámek; jinak vrátí hodnotu nula.