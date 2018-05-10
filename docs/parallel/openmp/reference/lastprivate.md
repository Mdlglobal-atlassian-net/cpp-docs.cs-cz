---
title: lastprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aaf80e3061877c42154ab9ee5ccd30f47f17135
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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