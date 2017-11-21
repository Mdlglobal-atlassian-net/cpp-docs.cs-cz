---
title: "asctime –, _wasctime – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wasctime
- asctime
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
- _tasctime
- asctime
- _wasctime
dev_langs: C++
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e356e6bef6c46bfede3f8337969fd1385cebd66
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="asctime-wasctime"></a>asctime, _wasctime
Převést `tm` čas struktura na řetězec znaků. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [asctime_s –, _wasctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *asctime(   
   const struct tm *timeptr   
);  
wchar_t *_wasctime(   
   const struct tm *timeptr   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timeptr`  
 Struktura času a data.  
  
## <a name="return-value"></a>Návratová hodnota  
 `asctime`vrací ukazatel na výsledném řetězci znaků; `_wasctime` vrací ukazatel na řetězec znaků celou výsledek. Není k dispozici žádnou návratovou hodnotu chyby.  
  
## <a name="remarks"></a>Poznámky  
 Bezpečnější verze tyto funkce jsou k dispozici. v tématu [asctime_s –, _wasctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md).  
  
 `asctime` Funkce převede čas uložené jako struktura na řetězec znaků. `timeptr` Hodnota se obvykle získávají z volání `gmtime` nebo `localtime`, které oba vrátit ukazatel na `tm` struktura, definované v čase. H.  
  
|člen timeptr|Hodnota|  
|--------------------|-----------|  
|`tm_hour`|Hodiny od půlnoci (0-23)|  
|`tm_isdst`|Kladné, pokud letní čas je v platnosti; 0, pokud letní čas není platný; záporná, pokud má neznámý stav letní čas. Běhové knihovny jazyka C předpokládá Spojené státy pravidla pro implementaci výpočtu letní čas (DST).|  
|`tm_mday`|Den v měsíci (1-31)|  
|`tm_min`|Počet minut po hodině (0-59)|  
|`tm_mon`|Měsíc (0-11; Ledna = 0)|  
|`tm_sec`|Sekund za minutu (0-59)|  
|`tm_wday`|Den v týdnu (0-6; Neděle = 0)|  
|`tm_yday`|Den v roce (0-365; 1. ledna = 0)|  
|`tm_year`|Rok (aktuálního roku minus 1900)|  
  
 Řetězec převedený znaků se také upraví podle nastavení zóny Místní čas. Informace o konfiguraci místního času najdete v tématu [čas](../../c-runtime-library/reference/time-time32-time64.md), [_ftime –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), a [místní čas](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) funkce a [_tzset –](../../c-runtime-library/reference/tzset.md) – funkce informace o definování časové pásmo prostředí a globální proměnné.  
  
 Výsledek řetězec produkovaný `asctime` obsahuje přesně 26 znaků a má tvar `Wed Jan 02 02:03:55 1980\n\0`. 24 hodin se používá. Všechna pole mít konstantní šířky. Znak nového řádku a znak hodnoty null zabírají posledních dvou pozic řetězce. `asctime`jeden, staticky přidělené vyrovnávací paměti se používá k ukládání vrácený řetězec. Každé volání této funkce zničí výsledek předchozí volání.  
  
 `_wasctime`široká charakterová verze `asctime`. `_wasctime`a `asctime` chovat jinak shodně.  
  
 Tyto funkce ověřit jejich parametrů. Pokud `timeptr` je ukazatel s hodnotou null, nebo pokud obsahuje hodnoty out-of-range, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `NULL` a nastaví `errno` k `EINVAL`.  
  
### <a name="generic-text-routine-mapping"></a>Rutiny mapování obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tasctime`|`asctime`|`asctime`|`_wasctime`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`asctime`|\<Time.h >|  
|`_wasctime`|\<Time.h > nebo \<wchar.h >|  
  
## <a name="example"></a>Příklad  
 Tento program umístí systémového času v dlouhých celých čísel `aclock`, překládá do struktury `newtime` a převede jej na řetězec formulář pro výstup, pomocí `asctime` funkce.  
  
```  
// crt_asctime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
    struct tm   *newTime;  
    time_t      szClock;  
  
    // Get time in seconds  
    time( &szClock );  
  
    // Convert time to struct tm form   
    newTime = localtime( &szClock );  
  
    // Print local time as a string.  
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996  
    // Note: asctime is deprecated; consider using asctime_s instead  
}  
```  
  
```Output  
Current date and time: Sun Feb 03 11:38:58 2002  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [CTime –, _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 –](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime – _ftime32 –, _ftime64 –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset –](../../c-runtime-library/reference/tzset.md)   
 [asctime_s –, _wasctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md)