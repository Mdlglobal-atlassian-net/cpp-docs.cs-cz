---
title: konstanty jazyka _locking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
dev_langs:
- C++
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4231235fc35a8b6d22f49e2ba05db337a619713
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="locking-constants"></a>Konstanty jazyka _locking
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <sys/locking.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 *Režimu* argument ve volání `_locking` funkce určuje uzamčení akce má být provedena.  
  
 *Režimu* argument musí být jeden z následujících manifestu konstanty.  
  
 `_LK_LOCK`  
 Zamkne zadaný počet bajtů. Pokud počet bajtů nelze zamknout, funkce se pokusí znovu po 1 sekunda. Pokud po 10 pokusy o, nelze jej zamknout počet bajtů, funkce vrátí chybu.  
  
 `_LK_RLCK`  
 Stejné jako `_LK_LOCK`.  
  
 `_LK_NBLCK`  
 Zamkne zadaný počet bajtů. Pokud nelze zamknout bajtů, funkce vrátí chybu.  
  
 `_LK_NBRLCK`  
 Stejné jako `_LK_NBLCK`.  
  
 `_LK_UNLCK`  
 Odemkne zadaný počet bajtů. (Počet bajtů musí byla dříve uzamčena.)  
  
## <a name="see-also"></a>Viz také  
 [_locking –](../c-runtime-library/reference/locking.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)