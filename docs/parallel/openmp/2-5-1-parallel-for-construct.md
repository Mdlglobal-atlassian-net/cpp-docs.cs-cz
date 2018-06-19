---
title: 2.5.1 parallel for – konstrukce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef2732c4f8713466d282346ea240bd3c41886ce0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687150"
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