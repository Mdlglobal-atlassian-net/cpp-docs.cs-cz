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
ms.workload: cplusplus
ms.openlocfilehash: 8fcdacdbb38a9bb27e35ada74aa2139be10c6797
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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