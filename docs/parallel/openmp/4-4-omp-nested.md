---
title: 4.4 OMP_NESTED | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50b2b110f191252702da9a2b6eed99baa40b7814
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
`OMP_NESTED` Proměnnou prostředí povolí nebo zakáže vnořené paralelismus, není-li povolit nebo zakázat při volání vnořené paralelismus `o` **mp_set_nested** rutiny knihovny. Pokud nastavena na **TRUE**, je povoleno vnořené paralelismus; Pokud je nastaven na hodnotu **FALSE**, vnořených paralelismus je zakázána. Výchozí hodnota je **FALSE**.  
  
 Příklad:  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>Mezi odkaz:  
  
-   `omp_set_nested`Funkce, najdete v části [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40.