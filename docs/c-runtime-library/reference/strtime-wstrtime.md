---
title: "_strtime –, _wstrtime – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wstrtime
- _strtime
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
dev_langs: C++
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9554272eda10c77dcbb464904897f47729b45f44
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strtime-wstrtime"></a>_strtime, _wstrtime
Kopírování času do vyrovnávací paměti. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_strtime_s –, _wstrtime_s –](../../c-runtime-library/reference/strtime-s-wstrtime-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_strtime(  
   char *timestr   
);  
wchar_t *_wstrtime(  
   wchar_t *timestr   
);  
template <size_t size>  
char *_strtime(  
   char (&timestr)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wstrtime(  
   wchar_t (&timestr)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `timestr`  
 Řetězce času.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na výsledný řetězec znaků `timestr`.  
  
## <a name="remarks"></a>Poznámky  
 `_strtime` Funkce zkopíruje aktuálním místním časem do vyrovnávací paměti, na kterou odkazuje `timestr`. Formát času je jako `hh:mm:ss` kde `hh` je dvě číslice představující hodinu ve 24hodinovém formátu `mm` je dvě číslice představující minut po hodině, a `ss` je dvě číslice představující sekund. Například řetězec `18:23:44` představuje 23 minut a 44 sekund po 6 hodin Vyrovnávací paměti musí být minimálně 9 bajtů.  
  
 `_wstrtime`široká charakterová verze `_strtime`; argument a vrátí hodnotu `_wstrtime` jsou široká charakterová řetězce. Tyto funkce chovají stejně jako jinak. Pokud `timestr` je `NULL` ukazatel nebo, pokud `timestr` je v nesprávném formátu, neplatný parametr rutina je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud výjimka může pokračovat, tyto funkce vrátí hodnotu NULL a sadu `errno` k `EINVAL` Pokud `timestr` byla NULL nebo nastavte `errno` k `ERANGE` Pokud `timestr` je v nesprávném formátu.  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstrtime`|`_strtime`|`_strtime`|`_wstrtime`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_strtime`|\<Time.h >|  
|`_wstrtime`|\<Time.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_strtime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char tbuffer [9];  
   _strtime( tbuffer ); // C4996  
   // Note: _strtime is deprecated; consider using _strtime_s instead  
   printf( "The current time is %s \n", tbuffer );  
}  
```  
  
```Output  
The current time is 14:21:44  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime –, _wasctime –](../../c-runtime-library/reference/asctime-wasctime.md)   
 [CTime –, _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 –](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [mktime – _mktime32 –, _mktime64 –](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset –](../../c-runtime-library/reference/tzset.md)