---
title: 2.5.2 parallel sections – konstrukce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6f7a84e322cb273733c6a724ee2563928df8362
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections – konstrukce
**Parallel sections –** – direktiva nabízí způsob zástupce pro zadání **paralelní** oblast obsahující pouze jeden **části** – direktiva. Sémantika jsou shodné s explicitním zadáním **paralelní** – direktiva bezprostředně následované **části** – direktiva. Syntaxe **parallel sections –** – Direktiva vypadá takto:  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-linestructured-block  ]  
   ...  
}  
```  
  
 *Klauzule* může být jedna z klauzule akceptovat **paralelní** a **části** direktivy, s výjimkou **nowait** klauzule.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **paralelní** direktivy, viz [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.  
  
-   **části** direktivy, viz [části 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) na stránce 14.