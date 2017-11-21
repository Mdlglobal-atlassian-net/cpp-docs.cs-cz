---
title: OMP_SCHEDULE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_SCHEDULE
dev_langs: C++
helpviewer_keywords: OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2295a801-e584-4d2f-826f-7ca4c88846a6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c29ec07f9a912fb66adc391465885da8030cc466
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ompschedule"></a>OMP_SCHEDULE
Mění chování [plán](../../../parallel/openmp/reference/schedule.md) klauzule při `schedule(runtime)` je uveden v `for` nebo `parallel for` – direktiva.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
set OMP_SCHEDULE[=type[,size]]  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `size`(volitelné)  
 Určuje velikost iterací. `size`musí být kladné celé číslo. Výchozí hodnota je 1, ale když `type` je statický. Pokud `type` je `runtime`.  
  
 `type`  
 Druh plánování:  
  
-   `dynamic`  
  
-   `guided`  
  
-   `runtime`  
  
-   `static`  
  
## <a name="remarks"></a>Poznámky  
 Výchozí hodnota v implementaci Visual C++ standardní OpenMP je `OMP_SCHEDULE=static,0`.  
  
 Další informace najdete v tématu [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz nastaví **OMP_SCHEDULE** proměnnou prostředí:  
  
```  
set OMP_SCHEDULE="guided,2"  
```  
  
 Následující příkaz zobrazí aktuální nastavení **OMP_SCHEDULE** proměnnou prostředí:  
  
```  
set OMP_SCHEDULE  
```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné prostředí](../../../parallel/openmp/reference/openmp-environment-variables.md)