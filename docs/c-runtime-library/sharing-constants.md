---
title: Sdílení konstant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
dev_langs:
- C++
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41060a9dbd3d2bc8176a2b13233db54933a6428b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409700"
---
# <a name="sharing-constants"></a>Sdílení konstant
Konstanty pro sdílení souborů režimy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <share.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 *Shflag* argument určuje sdílení režimu, který se skládá z jedné nebo více manifestu konstanty. Ty mohou být kombinovány s *oflag* argumenty (viz [konstanty souboru](../c-runtime-library/file-constants.md)).  
  
 Následující tabulka uvádí konstanty a jejich význam:  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_SH_DENYRW`|Odmítne oprávnění ke čtení a zápisu do souboru|  
|`_SH_DENYWR`|Odmítne přístup k zápisu do souboru|  
|`_SH_DENYRD`|Odmítne přístup pro čtení k souboru|  
|`_SH_DENYNO`|Povolí přístup čtení a zápis|  
|`_SH_SECURE`|Nastaví zabezpečeném režimu (sdílené pro čtení, výhradní přístup pro zápis).|  
  
## <a name="see-also"></a>Viz také  
 [_sopen –, _wsopen –](../c-runtime-library/reference/sopen-wsopen.md)   
 [_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)