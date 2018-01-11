---
title: "3.3.1 omp_get_wtime – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f89a71d1b91a27dfdd0abf13be4a5f0e30b3fd9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime – funkce
`omp_get_wtime` Funkce vrátí hodnotu s plovoucí desetinnou Dvojitá přesnost rovno uplynulá skutečný čas v sekundách, protože některé "čas v minulosti".  Skutečný "čas v minulosti" je volitelný, ale je zaručeno nechcete změnit během provádění programu aplikace. Formát vypadá takto:  
  
```  
#include <omp.h>  
double omp_get_wtime(void);  
```  
  
 Předpokládá se, že funkce bude použit k měření procentuálně dobu, jak je znázorněno v následujícím příkladu:  
  
```  
double start;  
double end;  
start = omp_get_wtime();  
... work to be timed ...  
end = omp_get_wtime();  
printf_s("Work took %f sec. time.\n", end-start);  
```  
  
 Doby vrátil jsou "vlákno doby" ve které je určen, že nemusí být globálně konzistentní v rámci všechna vlákna podílejících se na aplikace.