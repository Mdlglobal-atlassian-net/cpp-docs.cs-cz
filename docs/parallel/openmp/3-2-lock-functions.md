---
title: 3.2 funkce uzamčení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd788b0ef1c72b1f38a44ee608ce0c7760e24adc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="32-lock-functions"></a>3.2 Funkce zamykání
Funkce popsané v této části upravit zámky používán k synchronizaci.  
  
 Pro následující funkce, musí mít proměnnou zámku typ **omp_lock_t**. Tato proměnná je nutno přistupovat pouze prostřednictvím těchto funkcí. Všechny funkce Zámek vyžadují argument, který má ukazatel na **omp_lock_t** typu.  
  
-   `omp_init_lock` Funkce inicializuje jednoduché zámku.  
  
-   `omp_destroy_lock` Funkce odebere jednoduché zámku.  
  
-   `omp_set_lock` Funkce čeká, dokud nebude k dispozici jednoduchý zámku.  
  
-   `omp_unset_lock` Funkce uvolní jednoduché zámek.  
  
-   `omp_test_lock` Funkce testy jednoduché zámku.  
  
 Pro následující funkce, musí mít proměnnou zámku typ **omp_nest_lock_t**.  Tato proměnná je nutno přistupovat pouze prostřednictvím těchto funkcí. Všechny funkce nestable zámku vyžadují argument, který má ukazatel na **omp_nest_lock_t** typu.  
  
-   `omp_init_nest_lock` Funkce inicializuje nestable zámku.  
  
-   `omp_destroy_nest_lock` Funkce odebere nestable zámku.  
  
-   `omp_set_nest_lock` Funkce čeká, dokud nebude k dispozici nestable zámku.  
  
-   `omp_unset_nest_lock` Funkce uvolní nestable zámek.  
  
-   `omp_test_nest_lock` Funkce testy nestable zámku.  
  
 Funkce Zámek OpenMP přístup k proměnné zámku tak, že vždy číst a aktualizovat nejnovější hodnotu proměnné zámku. Proto není nutné u programu OpenMP zahrnout explicitní **vyprázdnění** direktivy pro zajištění konzistence mezi různých vláknech hodnota proměnné zámku. (Může být potřeba **vyprázdnění** direktivy aby hodnoty jiných proměnných konzistentní.)