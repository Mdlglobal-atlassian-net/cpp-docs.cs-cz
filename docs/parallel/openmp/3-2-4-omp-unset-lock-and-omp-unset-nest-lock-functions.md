---
title: "3.2.4 omp_unset_lock a omp_unset_nest_lock – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c7a3aebc404205c85627820188e137713317eb7d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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