---
title: 3.3.1 omp_get_wtime – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d71296d23df72464ed730713566c95e2403760a1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689490"
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