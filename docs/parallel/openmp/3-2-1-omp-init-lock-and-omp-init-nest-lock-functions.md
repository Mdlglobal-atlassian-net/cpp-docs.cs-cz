---
title: "3.2.1 omp_init_lock a omp_init_nest_lock – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e00772d4abb7fc72827a116d18c30940ade499db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock a omp_init_nest_lock – funkce
Tyto funkce poskytují jediným způsobem, inicializace zámek. Jednotlivé funkce inicializuje zámek spojené s parametrem *zámku* pro použití při následných voláních. Formát vypadá takto:  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Počáteční stav se odemkne (to znamená, žádný přístup z více vláken vlastní zámek). Na nestable zámek počáteční počet vnoření je nula. Je nekompatibilní volat buď tyto rutiny s zámku proměnné, která již byl inicializován.