---
title: "Konstanty matematické chyby | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
dev_langs: C++
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
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 003851227d56469436f7c75396803d80052dca15
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [_matherr –](../c-runtime-library/reference/matherr.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)