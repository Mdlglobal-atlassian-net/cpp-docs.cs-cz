---
title: "_strtime_s –, _wstrtime_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wstrtime_s
- _strtime_s
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
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
dev_langs: C++
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f7a2d8baac49543f09d3d2fa35764ae127f5507
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="strtimes-wstrtimes"></a>_strtime_s, _wstrtime_s
Zkopírujte aktuální čas do vyrovnávací paměti. Toto jsou verze [_strtime –, _wstrtime –](../../c-runtime-library/reference/strtime-wstrtime.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _strtime_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrtime_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strtime_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrtime_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`buffer`  
 Vyrovnávací paměť, minimálně 10 bajtů, kde budou zapsány čas.  
  
 [v]`numberOfElements`  
 Velikost vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu.  
  
 Pokud dojde k chybový stav, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v kód chyby. H; najdete v následující tabulce přesný chyby generované pomocí této funkce. Další informace o kódy chyb naleznete v tématu [errno – konstanty](../../c-runtime-library/errno-constants.md).  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`buffer`|`numberOfElements`|Vrátí|Obsah`buffer`|  
|--------------|------------------------|------------|--------------------------|  
|`NULL`|(všechny)|`EINVAL`|nedojde ke změně|  
|Není `NULL` (směřující do platné vyrovnávací paměti)|0|`EINVAL`|nedojde ke změně|  
|Není `NULL` (směřující do platné vyrovnávací paměti)|0 < velikost < 9|`EINVAL`|prázdný řetězec.|  
|Není `NULL` (směřující do platné vyrovnávací paměti)|Velikost > 9|0|Aktuální čas ve formátu podle specifikace v poznámkách|  
  
## <a name="security-issues"></a>Problémy se zabezpečením  
 Předávání v neplatný NENULOVOU hodnotu pro velikost vyrovnávací paměti bude výsledkem narušení přístupu, pokud `numberOfElements` parametr je větší než 9.  
  
 Předáním hodnoty `numberOfElements` , je větší než skutečná velikost vyrovnávací paměti bude mít za následek přetečení vyrovnávací paměti.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce zajistit bezpečnější verzích `_strtime` a `_wstrtime`. `_strtime_s` Funkce zkopíruje aktuálním místním časem do vyrovnávací paměti, na kterou odkazuje `timestr`. Formát času je jako `hh:mm:ss` kde `hh` je dvě číslice představující hodinu ve 24hodinovém formátu `mm` je dvě číslice představující minut po hodině, a `ss` je dvě číslice představující sekund. Například řetězec `18:23:44` představuje 23 minut a 44 sekund po 6 hodin Vyrovnávací paměti musí být minimálně 9 bajtů; Skutečná velikost je určena druhý parametr.  
  
 `_wstrtime`široká charakterová verze `_strtime`; argument a vrátí hodnotu `_wstrtime` jsou široká charakterová řetězce. Tyto funkce chovají stejně jako jinak.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mapping"></a>Mapování obecného textu rutiny:  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstrtime_s`|`_strtime_s`|`_strtime_s`|`_wstrtime_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_strtime_s`|\<Time.h >|  
|`_wstrtime_s`|\<Time.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// strtime_s.c  
  
#include <time.h>  
#include <stdio.h>  
  
int main()  
{  
    char tmpbuf[9];  
    errno_t err;  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    // Display operating system-style date and time.   
    err = _strtime_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
      exit(1);  
    }  
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );  
    err = _strdate_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );  
  
}  
```  
  
```Output  
OS time:            14:37:49  
OS date:            04/25/03  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime_s –, _wasctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime_s –, _ctime32_s –, _ctime64_s –, _wctime_s –, _wctime32_s –, _wctime64_s –](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime_s – _gmtime32_s –, _gmtime64_s –](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s – _localtime32_s –, _localtime64_s –](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime – _mktime32 –, _mktime64 –](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)