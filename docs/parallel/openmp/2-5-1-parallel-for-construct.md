---
title: "2.5.1 parallel for – konstrukce | Microsoft Docs"
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
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dcd763b68a78e11c3c33bf3d750a26e88ad02ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for – konstrukce
**Paralelní pro** – direktiva je zkratkou pro **paralelní** oblast, která obsahuje pouze jedinou **pro** – direktiva. Syntaxe **paralelní pro** – Direktiva vypadá takto:  
  
```  
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop  
```  
  
 Tato direktiva umožňuje všechny klauzulích **paralelní** – direktiva a **pro** direktivy, s výjimkou `nowait` klauzule identické významy a omezení. Sémantika jsou shodné s explicitním zadáním **paralelní** – direktiva bezprostředně následované **pro** – direktiva.  
  
## <a name="cross-references"></a>Křížové odkazy:  
  
-   **paralelní** direktivy, viz [části 2.3](../../parallel/openmp/2-3-parallel-construct.md) na stránce 8.  
  
-   **pro** direktivy, viz [části 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stránce 11.  
  
-   Klauzule atributů pro data, najdete v části [2.7.2 klauzule atributů pro sdílení dat](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.