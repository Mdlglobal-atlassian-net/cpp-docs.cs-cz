---
title: "sdílené (OpenMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 90491e6e8b415c79e21b4fa518f7e60327ac823e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
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