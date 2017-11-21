---
title: "_TRUNCATE – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _TRUNCATE
- TRUNCATE
dev_langs: C++
helpviewer_keywords:
- TRUNCATE constant
- _TRUNCATE constant
ms.assetid: ad093dbf-1aa5-4bd2-9268-efc68afd8434
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2f34ae91dc57675e01859842a6e23a65f41520c2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="truncate"></a>_TRUNCATE
Určuje chování zkracování řetězců.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <stdlib.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 `_TRUNCATE`umožňuje zkrácení chování při předávání jako `count` parametr na tyto funkce:  
  
 [strncpy_s –, _strncpy_s_l –, wcsncpy_s –, _wcsncpy_s_l –, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)  
  
 [strncat_s –, _strncat_s_l, wcsncat_s –, _wcsncat_s_l, _mbsncat_s –, _mbsncat_s_l –](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)  
  
 [mbstowcs_s –, _mbstowcs_s_l –](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)  
  
 [mbsrtowcs_s –](../c-runtime-library/reference/mbsrtowcs-s.md)  
  
 [wcstombs_s –, _wcstombs_s_l –](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)  
  
 [wcsrtombs_s –](../c-runtime-library/reference/wcsrtombs-s.md)  
  
 [_snprintf_s –, _snprintf_s_l –, _snwprintf_s –, _snwprintf_s_l –](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)  
  
 [vsnprintf_s –, _vsnprintf_s –, _vsnprintf_s_l –, _vsnwprintf_s –, _vsnwprintf_s_l –](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)  
  
 Pokud cílová vyrovnávací paměť je příliš malá, aby udržení celý řetězec, normální chování těchto funkcí je považováno za chyba (viz [ověření parametru](../c-runtime-library/parameter-validation.md)). Ale pokud je povolená zkracování řetězců předáním `_TRUNCATE`, tyto funkce budou kopírovat pouze na velikost řetězce, který se vejde ponechat cílové vyrovnávací paměti ukončené hodnotou null a vrátí úspěšně.  
  
 Řetězec zkrácení změní návratové hodnoty ovlivněných funkcí. Následující funkce vrátit 0 Pokud k žádnému zkrácení nebo `STRUNCATE` Pokud dojde ke zkrácení:  
  
 [strncpy_s –, _strncpy_s_l –, wcsncpy_s –, _wcsncpy_s_l –, _mbsncpy_s, _mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)  
  
 [strncat_s –, _strncat_s_l, wcsncat_s –, _wcsncat_s_l, _mbsncat_s –, _mbsncat_s_l –](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)  
  
 [wcstombs_s –, _wcstombs_s_l –](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)  
  
 [mbstowcs_s –, _mbstowcs_s_l –](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)  
  
 Následující funkce vrátí počet znaků, pokud k žádnému zkrácení zkopíruje nebo -1, pokud dojde k zkrácení (párování chování původní snprintf – funkce):  
  
 [_snprintf_s –, _snprintf_s_l –, _snwprintf_s –, _snwprintf_s_l –](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)  
  
 [vsnprintf_s –, _vsnprintf_s –, _vsnprintf_s_l –, _vsnwprintf_s –, _vsnwprintf_s_l –](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)  
  
## <a name="example"></a>Příklad  
  
```  
// crt_truncate.c  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
   char src[] = "1234567890";  
   char dst[5];  
   errno_t err = strncpy_s(dst, _countof(dst), src, _TRUNCATE);  
   if ( err == STRUNCATE )  
      printf( "truncation occurred!\n" );  
   printf( "'%s'\n", dst );  
}  
```  
  
```Output  
truncation occurred!  
'1234'  
```  
  
## <a name="see-also"></a>Viz také  
 [Globální konstanty](../c-runtime-library/global-constants.md)