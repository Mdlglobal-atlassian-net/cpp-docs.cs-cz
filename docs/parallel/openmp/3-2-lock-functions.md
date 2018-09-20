---
title: 3.2 funkce uzamčení | Dokumentace Microsoftu
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
ms.openlocfilehash: 97f125129d4b35586111f3d4092d457560aaebec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412272"
---
# <a name="32-lock-functions"></a>3.2 Funkce zamykání

Funkce popsané v této části manipulovat s zámky používán k synchronizaci.

Pro následující funkce, proměnná zámku musí být typu **omp_lock_t**. Tato proměnná musí být přístupný pouze prostřednictvím těchto funkcí. Všechny funkce zamykání vyžaduje argument, který se má ukazatel na **omp_lock_t** typu.

- `omp_init_lock` Funkce inicializuje jednoduchým zámkem.

- `omp_destroy_lock` Funkce odstraní jednoduchým zámkem.

- `omp_set_lock` Funkce počká, dokud jednoduchým zámkem je k dispozici.

- `omp_unset_lock` Funkce uvolní jednoduchým zámkem.

- `omp_test_lock` Otestuje jednoduchým zámkem.

Pro následující funkce, proměnná zámku musí být typu **omp_nest_lock_t**.  Tato proměnná musí být přístupný pouze prostřednictvím těchto funkcí. Všechny funkce, vnořitelných zámku musí argument, který se má ukazatel na **omp_nest_lock_t** typu.

- `omp_init_nest_lock` Funkce inicializuje, vnořitelných zámek.

- `omp_destroy_nest_lock` Funkce odstraní, vnořitelných zámek.

- `omp_set_nest_lock` Funkce počká, dokud, vnořitelných zámek je k dispozici.

- `omp_unset_nest_lock` Funkce uvolní, vnořitelných zámek.

- `omp_test_nest_lock` Funkce testuje, vnořitelných zámek.

Funkce jazyka OpenMP zámek přístup k proměnné zámek takovým způsobem, jsou vždy číst a aktualizovat aktuální hodnotu proměnné zámku. Proto není nutné pro aplikaci OpenMP zahrnout explicitní **vyprázdnění** direktivy pro zajištění konzistence mezi vlákny hodnota proměnné zámku. (Může být potřeba **vyprázdnění** direktivy, aby byly hodnoty jiné proměnné konzistentní.)