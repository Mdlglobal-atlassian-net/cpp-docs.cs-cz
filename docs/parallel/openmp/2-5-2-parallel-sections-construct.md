---
title: "2.5.2 parallel sections – konstrukce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 086552c72e37822920e0afa213c7966befa052f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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