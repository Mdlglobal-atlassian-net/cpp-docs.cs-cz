---
title: Konstanty matematické chyby | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
dev_langs:
- C++
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb491e8073acf2af525814b595ce79365df0fa1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="math-error-constants"></a>Konstanty matematické chyby
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Matematické rutiny běhové knihovny můžete vygenerovat konstanty matematické chyby.  
  
 Typy výjimek definované v MATEMATICKÉ odpovídají tyto chyby popsané následujícím způsobem. H a jsou vrácené `_matherr` funkce při matematické chyby.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_DOMAIN`|Argument funkce je mimo doménu funkce.|  
|`_OVERFLOW`|Výsledek je příliš velký a nelze v návratového typu funkce.|  
|`_PLOSS`|Částečné ztrátě násobek došlo k chybě.|  
|`_SING`|Argument singularity: argument funkce má neplatnou hodnotu. (Například hodnota 0 je předaná do funkce, který vyžaduje nenulovou hodnotu.)|  
|`_TLOSS`|Celkový počet ztrátě násobek došlo k chybě.|  
|`_UNDERFLOW`|Výsledkem je, a nelze je příliš malá.|  
  
## <a name="see-also"></a>Viz také  
 [_matherr](../c-runtime-library/reference/matherr.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)