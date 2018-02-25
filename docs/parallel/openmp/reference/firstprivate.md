---
title: firstprivate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0438d98467b7843b6f70e0d075dc3b61375c48ca
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="firstprivate"></a>firstprivate
Určuje, že každé vlákno má mít svou vlastní instanci proměnné a že proměnnou by měl být inicializovaný s hodnotu proměnné, protože existuje před paralelní konstrukce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
firstprivate(var)  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`var`|Proměnná mít instancí v každé vlákno a které bude inicializován s hodnotou proměnné, protože existuje před paralelní konstrukce. Pokud je zadán více než jednu proměnnou, oddělte názvy proměnných čárkou.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="remarks"></a>Poznámky  
 `firstprivate` platí pro následující direktivy:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [single](../../../parallel/openmp/reference/single.md)  
  
 Další informace najdete v tématu [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).  
  
## <a name="example"></a>Příklad  
 Příklad použití `firstprivate`, podívejte se na příklad v [privátní](../../../parallel/openmp/reference/private-openmp.md).  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)