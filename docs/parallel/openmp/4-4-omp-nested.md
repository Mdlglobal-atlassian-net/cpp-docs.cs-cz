---
title: 4.4 OMP_NESTED | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1779b75774a2177a0d6a4f0661406e28b479a7ee
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
`OMP_NESTED` Proměnnou prostředí povolí nebo zakáže vnořené paralelismus, není-li povolit nebo zakázat při volání vnořené paralelismus `o` **mp_set_nested** rutiny knihovny. Pokud nastavena na **TRUE**, je povoleno vnořené paralelismus; Pokud je nastaven na hodnotu **FALSE**, vnořených paralelismus je zakázána. Výchozí hodnota je **FALSE**.  
  
 Příklad:  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>Mezi odkaz:  
  
-   `omp_set_nested` Funkce, najdete v části [části 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stránce 40.