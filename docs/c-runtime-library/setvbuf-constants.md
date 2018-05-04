---
title: setvbuf – konstanty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
dev_langs:
- C++
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d4292ae29602b5890a167a3e2c29e460d65373f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="setvbuf-constants"></a>setvbuf – konstanty
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto konstanty představují typ vyrovnávací paměti pro `setvbuf`.  
  
 Možné hodnoty jsou uvedeny následující konstantami manifestu:  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_IOFBF`|Úplné ukládání do vyrovnávací paměti: vyrovnávací paměti zadané ve volání do `setvbuf` se používá a jeho velikost je jako zadaný v `setvbuf` volání. Pokud je ukazatel vyrovnávací paměti **NULL**, automaticky přiděleného zadaná velikost vyrovnávací paměti se používá.|  
|`_IOLBF`|Stejné jako `_IOFBF`.|  
|`_IONBF`|Bez vyrovnávací paměti se používá, bez ohledu na to argumenty volání `setvbuf`.|  
  
## <a name="see-also"></a>Viz také  
 [setbuf –](../c-runtime-library/reference/setbuf.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)