---
title: Barrier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf5b2cd9edf54e58c06e7d2a48529393cd3ced64
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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