---
title: copyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32137534a43eeb0b038eae547f9bc19283412159
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="copyin"></a>copyin
Umožňuje vláken pro přístup k hlavní vlákno hodnota [threadprivate](../../../parallel/openmp/reference/threadprivate.md) proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
copyin(var)  
```  
  
## <a name="remarks"></a>Poznámky  
 kde  
  
 `var`  
 `threadprivate` Proměnné, která bude inicializován s hodnotou proměnné v hlavní vlákno, protože existuje před paralelní konstrukce.  
  
## <a name="remarks"></a>Poznámky  
 `copyin` platí pro následující direktivy:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Oddíly](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Další informace najdete v tématu [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).  
  
## <a name="example"></a>Příklad  
 V tématu [threadprivate](../../../parallel/openmp/reference/threadprivate.md) příklad použití `copyin`.  
  
## <a name="see-also"></a>Viz také  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)