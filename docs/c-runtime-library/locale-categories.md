---
title: "Kategorie národního prostředí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
dev_langs: C++
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dd57f24bd6d790cc03c3e5bbb1e58ec45eee86e0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="locale-categories"></a>Kategorie národního prostředí
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <locale.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Kategorie národního prostředí se používá k určení, jaká část informací o národním prostředí program bude používat rutiny lokalizace manifestu konstanty. Národní prostředí odkazuje na polohu (nebo země nebo oblast), pro který lze přizpůsobit některé aspekty vašeho programu. Oblasti závislých na národním prostředí obsahovat, například formátování kalendářních dat nebo formát zobrazení pro peněžní hodnoty.  
  
|Kategorie národního prostředí|Součástí program vliv|  
|---------------------|-------------------------------|  
|`LC_ALL`|Všechny chování specifické národního prostředí (všechny kategorie)|  
|`LC_COLLATE`|Chování `strcoll` a `strxfrm` funkce|  
|`LC_CTYPE`|Chování funkce znak zpracování (s výjimkou **IsDigit –**, `isxdigit`, `mbstowcs`, a `mbtowc`, které jsou poškozena)|  
|`LC_MAX`|Stejné jako`LC_TIME`|  
|`LC_MIN`|Stejné jako`LC_ALL`|  
|`LC_MONETARY`|Měnovou formátování informace o vrácené `localeconv` – funkce|  
|`LC_NUMERIC`|Desetinnou znak pro formátovaný výstup rutiny (například `printf`), rutiny převodu dat a Neměnové formátování informace o vrácené `localeconv` – funkce|  
|`LC_TIME`|Chování `strftime` – funkce|  
  
 V tématu [setlocale _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) příklad.  
  
## <a name="see-also"></a>Viz také  
 [localeconv –](../c-runtime-library/reference/localeconv.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll – funkce](../c-runtime-library/strcoll-functions.md)   
 [STRFTIME –, wcsftime –, _strftime_l –, _wcsftime_l –](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm –, wcsxfrm –, _strxfrm_l –, _wcsxfrm_l –](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)