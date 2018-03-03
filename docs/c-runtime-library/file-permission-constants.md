---
title: "Konstanty oprávnění souboru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _S_IWRITE
- _S_IREAD
dev_langs:
- C++
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 123b5f14c6d13e7ee7ff41de00816234d6e45fc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="file-permission-constants"></a>Konstanty oprávnění souboru
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Jeden z těchto konstanty je požadován při `_O_CREAT` (`_open`, `_sopen`) je zadán.  
  
 `pmode` Argument určuje nastavení oprávnění souboru následujícím způsobem.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_S_IREAD`|Čtení povolené|  
|`_S_IWRITE`|Zápis povolen|  
|`_S_IREAD` &#124; `_S_IWRITE`|Čtení a zápis povolen.|  
  
 Když se použije jako `pmode` argument pro `_umask`, manifestu konstanta nastaví nastavení oprávnění následujícím způsobem.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_S_IREAD`|Zápis není povolený (soubor je jen pro čtení)|  
|`_S_IWRITE`|Čtení není povolené (soubor je jen pro zápis)|  
|`_S_IREAD` &#124; `_S_IWRITE`|Čtení ani zápis povolen.|  
  
## <a name="see-also"></a>Viz také  
 [_Otevřít _wopen –](../c-runtime-library/reference/open-wopen.md)   
 [_sopen –, _wsopen –](../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask –](../c-runtime-library/reference/umask.md)   
 [Standardní typy](../c-runtime-library/standard-types.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)