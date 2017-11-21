---
title: firstprivate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: firstprivate
dev_langs: C++
helpviewer_keywords: firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0645eee74ab162c444531c141b297665653907b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 `firstprivate`platí pro následující direktivy:  
  
-   [pro](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [paralelní](../../../parallel/openmp/reference/parallel.md)  
  
-   [oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
-   [jeden](../../../parallel/openmp/reference/single.md)  
  
 Další informace najdete v tématu [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).  
  
## <a name="example"></a>Příklad  
 Příklad použití `firstprivate`, podívejte se na příklad v [privátní](../../../parallel/openmp/reference/private-openmp.md).  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)