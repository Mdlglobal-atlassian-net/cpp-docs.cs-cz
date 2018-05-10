---
title: 3.2.1 omp_init_lock a omp_init_nest_lock – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f14e182e6c981cd5de7a4cf92d8c285a4b49c66
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock a omp_init_nest_lock – funkce
Tyto funkce poskytují jediným způsobem, inicializace zámek. Jednotlivé funkce inicializuje zámek spojené s parametrem *zámku* pro použití při následných voláních. Formát vypadá takto:  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Počáteční stav se odemkne (to znamená, žádný přístup z více vláken vlastní zámek). Na nestable zámek počáteční počet vnoření je nula. Je nekompatibilní volat buď tyto rutiny s zámku proměnné, která již byl inicializován.