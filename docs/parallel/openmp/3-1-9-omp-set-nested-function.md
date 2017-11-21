---
title: "3.1.9 omp_set_nested – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a70406e42904c40ac81901ffd174991c0ebc54d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested – funkce
**Omp_set_nested –** funkce povolí nebo zakáže vnořené stupně paralelního zpracování. Formát vypadá takto:  
  
```  
#include <omp.h>  
void omp_set_nested(int nested);  
```  
  
 Pokud *vnořené* hodnotu 0, vnořené paralelismus je zakázaná, který je výchozí a paralelní vnořené oblasti jsou serializovat a provedený aktuální vlákno. Pokud *vnořené* vyhodnotí vnořené paralelismus nenulovou hodnotu, je povolena a paralelní oblasti, které jsou vnořené může nasadit další vlákna na formuláři vnořené týmy.  
  
 Tato funkce má důsledky popsané výše při volání z části program kde **omp_in_parallel –** funkce vrátí hodnotu 0. Pokud je volána z část programu kde **omp_in_parallel –** funkce vrátí nenulovou hodnotu, chování tato funkce není definován.  
  
 Toto volání má vyšší prioritu než **OMP_NESTED** proměnné prostředí.  
  
 Pokud je povoleno vnořené paralelismus, počet vláken používaných provést paralelní vnořené oblastí je definované implementací. V důsledku toho jsou kompatibilní se standardem OpenMP implementace povoleny k serializaci vnořených paralelní oblasti i v případě, že je povolená vnořené paralelismus.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **OMP_NESTED** proměnné, naleznete v prostředí [části 4.4](../../parallel/openmp/4-4-omp-nested.md) na stránce 49.  
  
-   **omp_in_parallel –** funkce najdete v tématu [části 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stránce 38.