---
title: lastprivate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7945edb879d81bb50753619c1206b9da575dbcda
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="lastprivate"></a>lastprivate
Určuje, že je nastavena nadřazených kontext verzi proměnnou rovna privátní verzi kteroukoli vlákna spustí poslední iterace (konstrukce cyklu for) nebo poslední část (#pragma oddíly).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
lastprivate(var)  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `var`  
 Proměnné, která je nastavena na privátní verzi kteroukoli vlákna spustí poslední iterace (konstrukce cyklu for) nebo poslední část (#pragma oddíly).  
  
## <a name="remarks"></a>Poznámky  
 `lastprivate` platí pro následující direktivy:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Další informace najdete v tématu [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).  
  
## <a name="example"></a>Příklad  
 V tématu [plán](../../../parallel/openmp/reference/schedule.md) příklad použití `lastprivate` klauzule.  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)