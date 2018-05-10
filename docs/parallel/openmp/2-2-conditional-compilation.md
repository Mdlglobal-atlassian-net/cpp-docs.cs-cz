---
title: 2.2 Podmíněná kompilace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3d8c7073548c015d9982b721387176a0ca658c2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="22-conditional-compilation"></a>2.2 Podmíněná kompilace
_**OPENMP** název makra definované kompatibilní se standardem OpenMP implementace jako decimal konstanta *yyyymm*, která bude za rok a měsíc schválené specifikace. Toto makro nesmí být předmět **#define** nebo **#undef** předběžného zpracování direktiva.  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 Pokud dodavatelé definovat rozšíření do OpenMP, se může zadat další předdefinovaná makra.