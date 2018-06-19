---
title: konstanty jazyka _locking | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 588c286cbad5e0097394a38eed34c09fc04af3ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389966"
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