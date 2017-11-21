---
title: "2.2 Podmíněná kompilace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ddfb754e3aa4142b6d070f2b5fe20ac7a63512e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="22-conditional-compilation"></a>2.2 Podmíněná kompilace
_**OPENMP** název makra definované kompatibilní se standardem OpenMP implementace jako decimal konstanta *yyyymm*, která bude za rok a měsíc schválené specifikace. Toto makro nesmí být předmět **#define** nebo **#undef** předběžného zpracování direktiva.  
  
```  
#ifdef _OPENMP  
iam = omp_get_thread_num() + index;  
#endif  
```  
  
 Pokud dodavatelé definovat rozšíření do OpenMP, se může zadat další předdefinovaná makra.