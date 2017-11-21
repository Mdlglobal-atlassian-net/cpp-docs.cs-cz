---
title: 4.4 OMP_NESTED | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbb45bb04db612451c7d081f3a7afad8031da643
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
`OMP_NESTED` Proměnnou prostředí povolí nebo zakáže vnořené paralelismus, není-li povolit nebo zakázat při volání vnořené paralelismus `o` **mp_set_nested** rutiny knihovny. Pokud nastavena na **TRUE**, je povoleno vnořené paralelismus; Pokud je nastaven na hodnotu **FALSE**, vnořených paralelismus je zakázána. Výchozí hodnota je **FALSE**.  
  
 Příklad:  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>Mezi odkaz:  
  
-   `omp_set_nested`Funkce, najdete v části [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40.