---
title: "3.2 funkce uzamčení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 540c76a5fdcee4df78df454fed957191fc244cf5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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