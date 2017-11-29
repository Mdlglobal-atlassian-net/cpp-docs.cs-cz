---
title: "_stat – struktura, st_mode – konstanty pole | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- S_IFCHR
- S_IFDIR
- _S_IWRITE
- S_IFMT
- _S_IFDIR
- _S_IREAD
- S_IEXEC
- _S_IEXEC
- _S_IFMT
- S_IWRITE
- S_IFREG
- S_IREAD
- _S_IFCHR
- _S_IFREG
dev_langs: C++
helpviewer_keywords:
- S_IFDIR constant
- stat structure
- S_IWRITE constant
- S_IEXEC constant
- _S_IFREG constant
- S_IREAD constant
- stat structure, constants
- _S_IFMT constant
- st_mode field constants
- S_IFMT constant
- _S_IEXEC constant
- _S_IWRITE constant
- _S_IFDIR constant
- S_IFREG constant
- S_IFCHR constant
- _S_IREAD constant
- _S_IFCHR constant
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eb6277eea45aec64c285c3e2780d65be0224ce11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stat-structure-stmode-field-constants"></a>_stat – struktura, st_mode – konstanty pole
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 K označení typ souboru v se používají tyto konstanty **st_mode –** pole z [_stat – struktura](../c-runtime-library/standard-types.md).  
  
 Konstanty bitová maska jsou následující:  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_S_IFMT`|Maska typu souboru|  
|`_S_IFDIR`|Adresář|  
|`_S_IFCHR`|Speciální znak (označuje zařízení, pokud nastavení)|  
|`_S_IFREG`|Regulární|  
|`_S_IREAD`|Oprávnění ke čtení, vlastník|  
|`_S_IWRITE`|Oprávnění zapisovat, vlastník|  
|`_S_IEXEC`|Spuštění nebo vyhledávání oprávnění vlastníka|  
  
## <a name="see-also"></a>Viz také  
 [_stat, _wstat – funkce](../c-runtime-library/reference/stat-functions.md)   
 [_fstat –, _fstat32 –, _fstat64 –, _fstati64 –, _fstat32i64 –, _fstat64i32 –](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [Standardní typy](../c-runtime-library/standard-types.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)