---
title: Barrier | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0008c343130bf47170957204793cf3c85b22f1e3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="barrier"></a>barrier
Synchronizuje všechna vlákna v týmu; všechna vlákna pozastaví při bariéry, dokud všechna vlákna provést bariéry.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp barrier  
```  
  
## <a name="remarks"></a>Poznámky  
 `barrier` – Direktiva podporuje žádné OpenMP – klauzule.  
  
 Další informace najdete v tématu [2.6.3 barrier – direktiva](../../../parallel/openmp/2-6-3-barrier-directive.md).  
  
## <a name="example"></a>Příklad  
 Příklad, jak pomocí `barrier`, najdete v části [hlavní](../../../parallel/openmp/reference/master.md).  
  
## <a name="see-also"></a>Viz také  
 [Direktivy](../../../parallel/openmp/reference/openmp-directives.md)