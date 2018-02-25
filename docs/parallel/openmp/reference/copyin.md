---
title: copyin | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae680b2af468b9b11a7d2de44966ad554eec0150
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
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