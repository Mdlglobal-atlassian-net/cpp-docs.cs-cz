---
title: "OpenMP – klauzule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a63dacb8da2b7c4b1c7264cfccc6d2839db1b8b1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="openmp-clauses"></a>OpenMP – klauzule
Obsahuje odkazy na používá v rozhraní API OpenMP – klauzule.  
  
 Visual C++ podporuje následující klauzule OpenMP:  
  
|Klauzule|Popis|  
|------------|-----------------|  
|[copyin](../../../parallel/openmp/reference/copyin.md)|Umožňuje vláken pro přístup k hlavní vlákno hodnota [threadprivate](../../../parallel/openmp/reference/threadprivate.md) proměnné.|  
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|Určuje, že jeden nebo více proměnných by měl sdílen všechna vlákna.|  
|[default](../../../parallel/openmp/reference/default-openmp.md)|Určuje chování bez ohledu na obor proměnné v paralelní oblasti.|  
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|Určuje, že každé vlákno má mít svou vlastní instanci proměnné a že proměnnou by měl být inicializovaný s hodnotu proměnné, protože existuje před paralelní konstrukce.|  
|[if](../../../parallel/openmp/reference/if-openmp.md)|Určuje, zda se má provést smyčku paralelně nebo postupně.|  
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|Určuje, že je nastavena nadřazených kontext verzi proměnnou rovna privátní verzi kteroukoli vlákna spustí poslední iterace (konstrukce cyklu for) nebo poslední část (#pragma oddíly).|  
|[nowait](../../../parallel/openmp/reference/nowait.md)|Přepíše implicitní v direktivě bariéry.|  
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|Nastaví počet vláken v týmu přístup z více vláken.|  
|[řazení](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|Na paralelní vyžaduje [pro](../../../parallel/openmp/reference/for-openmp.md) příkaz Pokud [seřazené](../../../parallel/openmp/reference/ordered-openmp-directives.md) – direktiva má být použita ve smyčce.|  
|[private](../../../parallel/openmp/reference/private-openmp.md)|Určuje, že každé vlákno má mít svou vlastní instanci proměnné.|  
|[reduction](../../../parallel/openmp/reference/reduction.md)|Určuje, že jeden nebo více proměnných, které jsou soukromé pro každé vlákno jsou předmětem snížení operaci na konci paralelní oblast.|  
|[schedule](../../../parallel/openmp/reference/schedule.md)|Platí pro [pro](../../../parallel/openmp/reference/for-openmp.md) – direktiva.|  
|[shared](../../../parallel/openmp/reference/shared-openmp.md)|Určuje, že jeden nebo více proměnných by měl sdílen všechna vlákna.|  
  
## <a name="see-also"></a>Viz také  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Direktivy](../../../parallel/openmp/reference/openmp-directives.md)