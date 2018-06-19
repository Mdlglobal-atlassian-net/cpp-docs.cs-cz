---
title: sdílené (OpenMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8287f96f80748272e29b22ed5c43c364f4353b86
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691674"
---
# <a name="shared-openmp"></a>shared (OpenMP)
Určuje, že jeden nebo více proměnných by měl sdílen všechna vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
shared(var)  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `var`  
 Jeden další proměnné, do sdílené složky. Pokud je zadán více než jednu proměnnou, oddělte názvy proměnných čárkou.  
  
## <a name="remarks"></a>Poznámky  
 Jiný způsob, jak sdílet proměnné mezi vláken je s [copyprivate](../../../parallel/openmp/reference/copyprivate.md) klauzule.  
  
 `shared` platí pro následující direktivy:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Další informace najdete v tématu [2.7.2.4 sdílené](../../../parallel/openmp/2-7-2-4-shared.md).  
  
## <a name="example"></a>Příklad  
 V tématu [privátní](../../../parallel/openmp/reference/private-openmp.md) příklad použití `shared`.  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)