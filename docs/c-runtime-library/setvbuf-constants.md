---
title: "setvbuf – konstanty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _IOFBF
- _IONBF
- _IOLBF
dev_langs: C++
helpviewer_keywords:
- _IOFBF constant
- IOFBF constant
- IONBF constant
- _IOLBF constant
- IOLBF constant
- _IONBF constant
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 16a5a215657a6d447c43c7ba327ef0d5f31d4abb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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