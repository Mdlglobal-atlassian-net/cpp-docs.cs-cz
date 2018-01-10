---
title: "localtime_s – _localtime32_s –, _localtime64_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _localtime64_s
- _localtime32_s
- localtime_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
dev_langs: C++
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ddce7d73919e7e7942d8ddd7954ce6cbec4789fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="localtimes-localtime32s-localtime64s"></a>localtime_s, _localtime32_s, _localtime64_s
Převede hodnotu času a opravuje pro místní časovou zónu. Toto jsou verze [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t localtime_s(  
   struct tm* _tm,  
   const time_t *time   
);  
errno_t _localtime32_s(  
   struct tm* _tm,  
   const time32_t *time   
);  
errno_t _localtime64_s(  
   struct tm* _tm,  
   const _time64_t *time   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_tm`  
 Ukazatel na strukturu čas k vyplnění.  
  
 `time`  
 Ukazatel na uložené čas.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu. Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v Errno.h. Seznam těchto chybách naleznete v tématu [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`_tm`|`time`|Návratová hodnota|Hodnota v`_tm`|Vyvolá obslužnou rutinu neplatný parametr|  
|-----------|------------|------------------|--------------------|---------------------------------------|  
|`NULL`|všechny|`EINVAL`|nedojde ke změně|Ano|  
|Není `NULL` (odkazuje na platný paměti)|`NULL`|`EINVAL`|Všechna pole nastavena na hodnotu -1|Ano|  
|Není `NULL` (odkazuje na platný paměti)|menší než 0 nebo větší než`_MAX__TIME64_T`|`EINVAL`|Všechna pole nastavena na hodnotu -1|Ne|  
  
 V případě první dvě chybové stavy, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_localtime32_s` Funkce převede čas uložené jako [time_t](../../c-runtime-library/standard-types.md) hodnotu a výsledek je uložen ve struktuře typu `tm`. `long` Hodnota `timer` představuje počet sekund uběhlých od půlnoci (00: 00:00), 1. ledna 1970, UTC. Tato hodnota se obvykle získávají z `time` funkce.  
  
 `_localtime32_s`pro místní časové pásmo opraví, pokud uživatel nejprve nastaví proměnnou prostředí globální `TZ`. Když `TZ` nastavena, tři další systémové proměnné (`_timezone`, `_daylight`, a `_tzname`) se nastaví automaticky také. Pokud `TZ` proměnná není nastavena, `localtime32_s` pokusí použít informace o časovém pásmu, který je zadán v aplikaci datum a čas v Ovládacích panelech. Pokud tyto informace nelze získat, PST8PDT, která označuje, že tichomořském časovém pásmu, se používá ve výchozím nastavení. V tématu [_tzset –](../../c-runtime-library/reference/tzset.md) popis těchto proměnných. `TZ`rozšíření Microsoft a není součástí standardní definice ANSI `localtime`.  
  
> [!NOTE]
>  Cílové prostředí by měl pokusit určit, zda je v platnosti letní čas.  
  
 `_localtime64_s`, které používá `__time64_t` struktury, umožňuje data, která se vyjádřit až do 23:59:59, leden 18 3001, koordinovaný světový čas (UTC), zatímco `_localtime32_s` představuje datům až 23:59:59 18 leden 2038 UTC.  
  
 `localtime_s`Vložená funkce, jehož výsledkem je `_localtime64_s`, a `time_t` je ekvivalentní `__time64_t`. Pokud potřebujete vynutit kompilátoru interpretovat `time_t` jako starý 32bitovou verzi `time_t`, můžete definovat `_USE_32BIT_TIME_T`. Provedete to způsobí, že `localtime_s` k vyhodnocení `_localtime32_s`. Není doporučeno, protože vaše aplikace může selhat po 18. ledna 2038, a není povoleno na 64bitových platformách.  
  
 Pole typu Struktura [tm](../../c-runtime-library/standard-types.md) ukládat následující hodnoty, z nichž každý je `int`.  
  
 `tm_sec`  
 Sekund za minutu (0 - 59).  
  
 `tm_min`  
 Počet minut po hodině (0 - 59).  
  
 `tm_hour`  
 Hodiny po půlnoci (0 - 23).  
  
 `tm_mday`  
 Den v měsíci (1-31).  
  
 `tm_mon`  
 Měsíc (0 - 11; Ledna = 0).  
  
 `tm_year`  
 Rok (aktuálního roku minus 1900).  
  
 `tm_wday`  
 Den v týdnu (0 - 6; Neděle = 0).  
  
 `tm_yday`  
 Den v roce (0 - 365; 1. ledna = 0).  
  
 `tm_isdst`  
 Kladnou hodnotu, pokud letní čas je v platnosti; 0, pokud letní čas není platný; Pokud má neznámý stav letní čas zápornou hodnotu. Pokud `TZ` proměnná prostředí je nastavena, běhové knihovny jazyka C předpokládá pravidla vhodné pro Spojené státy pro implementaci výpočtu letní čas (letní čas).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`localtime_s`|\<Time.h >|  
|`_localtime32_s`|\<Time.h >|  
|`_localtime64_s`|\<Time.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_localtime_s.c  
/* This program uses _time64 to get the current time   
 * and then uses _localtime64_s() to convert this time to a structure   
 * representing the local time. The program converts the result   
 * from a 24-hour clock to a 12-hour clock and determines the   
 * proper extension (AM or PM).  
 */  
  
#include <stdio.h>  
#include <string.h>  
#include <time.h>  
  
int main( void )  
{  
        struct tm newtime;  
        char am_pm[] = "AM";  
        __time64_t long_time;  
        char timebuf[26];  
        errno_t err;  
  
        // Get time as 64-bit integer.  
        _time64( &long_time );   
        // Convert to local time.  
        err = _localtime64_s( &newtime, &long_time );   
        if (err)  
        {  
            printf("Invalid argument to _localtime64_s.");  
            exit(1);  
        }  
        if( newtime.tm_hour > 12 )        // Set up extension.   
                strcpy_s( am_pm, sizeof(am_pm), "PM" );  
        if( newtime.tm_hour > 12 )        // Convert from 24-hour   
                newtime.tm_hour -= 12;    // to 12-hour clock.   
        if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.  
                newtime.tm_hour = 12;  
  
        // Convert to an ASCII representation.   
        err = asctime_s(timebuf, 26, &newtime);  
        if (err)  
        {  
           printf("Invalid argument to asctime_s.");  
           exit(1);  
        }  
        printf( "%.19s %s\n", timebuf, am_pm );  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
Fri Apr 25 01:19:27 PM  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime_s –, _wasctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [CTime –, _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 –](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [_ftime – _ftime32 –, _ftime64 –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime_s – _gmtime32_s –, _gmtime64_s –](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)
