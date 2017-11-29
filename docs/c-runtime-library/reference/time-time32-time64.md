---
title: "Doba, _time32 –, _time64 – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- time
- _time64
- _time32
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
- time
- _time64
- time/time
- time/_time32
- time/_time64
- _time32
dev_langs: C++
helpviewer_keywords:
- time32 function
- _time32 function
- _time64 function
- time functions
- system time
- time64 function
ms.assetid: 280e00f2-2b93-4ece-94cd-e048484c6cc7
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 04e1db45e10d738d0a4270e7f2a4d6c71698f707
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="time-time32-time64"></a>time, _time32, _time64
Získáte systémového času.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
time_t time(  
   time_t *timer   
);  
__time32_t _time32(  
   __time32_t *timer   
);  
__time64_t _time64(  
   __time64_t *timer   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `timer`  
 Ukazatel na umístění úložiště pro čas.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí čas jako uplynulé sekund od půlnoci 1. ledna 1970, nebo -1 v případě k chybě.  
  
## <a name="remarks"></a>Poznámky  
 `time` Funkce vrátí počet sekund uběhlých od půlnoci (00: 00:00), 1. ledna 1970, koordinovaný světový čas (UTC), podle systémových hodin. Návratová hodnota je uložen v umístění poskytují `timer`. Tento parametr může být `NULL`, v takovém případě není uložen návratovou hodnotu.  
  
 `time`představuje obálku pro `_time64` a `time_t` je ve výchozím nastavení odpovídá `__time64_t`. Pokud potřebujete vynutit kompilátoru interpretovat `time_t` jako starý 32bitovou verzi `time_t`, můžete definovat `_USE_32BIT_TIME_T`. Není doporučeno, protože vaše aplikace může selhat po 18. ledna 2038; použití této makro není povolena na 64bitových platformách.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`time`, `_time32`, `_time64`|C: \<time.h >, C++: \<ctime > nebo \<time.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_times.c  
// compile with: /W3  
// This program demonstrates these time and date functions:  
//      time         _ftime    ctime_s     asctime_s  
//      _localtime64_s    _gmtime64_s    mktime    _tzset  
//      _strtime_s     _strdate_s  strftime  
//  
// Also the global variable:  
//      _tzname  
//  
// Turn off deprecated unsafe CRT function warnings  
#define _CRT_SECURE_NO_WARNINGS 1  
  
#include <time.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <sys/types.h>  
#include <sys/timeb.h>  
#include <string.h>  
  
int main()  
{  
    char tmpbuf[128], timebuf[26], ampm[] = "AM";  
    time_t ltime;  
    struct _timeb tstruct;  
    struct tm today, gmt, xmas = { 0, 0, 12, 25, 11, 93 };  
    errno_t err;  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    // Display operating system-style date and time.   
    _strtime_s( tmpbuf, 128 );  
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );  
    _strdate_s( tmpbuf, 128 );  
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );  
  
    // Get UNIX-style time and display as number and string.   
    time( &ltime );  
    printf( "Time in seconds since UTC 1/1/70:\t%lld\n", (long long)ltime );  
    err = ctime_s(timebuf, 26, &ltime);  
    if (err)  
    {  
       printf("ctime_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "UNIX time and date:\t\t\t%s", timebuf );  
  
    // Display UTC.   
    err = _gmtime64_s( &gmt, &ltime );  
    if (err)  
    {  
       printf("_gmtime64_s failed due to an invalid argument.");  
    }  
    err = asctime_s(timebuf, 26, &gmt);  
    if (err)  
    {  
       printf("asctime_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "Coordinated universal time:\t\t%s", timebuf );  
  
    // Convert to time structure and adjust for PM if necessary.   
    err = _localtime64_s( &today, &ltime );  
    if (err)  
    {  
       printf("_localtime64_s failed due to an invalid argument.");  
       exit(1);  
    }  
    if( today.tm_hour >= 12 )  
    {  
   strcpy_s( ampm, sizeof(ampm), "PM" );  
   today.tm_hour -= 12;  
    }  
    if( today.tm_hour == 0 )  // Adjust if midnight hour.  
   today.tm_hour = 12;  
  
    // Convert today into an ASCII string   
    err = asctime_s(timebuf, 26, &today);  
    if (err)  
    {  
       printf("asctime_s failed due to an invalid argument.");  
       exit(1);  
    }  
  
    // Note how pointer addition is used to skip the first 11   
    // characters and printf is used to trim off terminating   
    // characters.  
    //  
    printf( "12-hour time:\t\t\t\t%.8s %s\n",  
       timebuf + 11, ampm );  
  
    // Print additional time information.   
    _ftime( &tstruct ); // C4996  
    // Note: _ftime is deprecated; consider using _ftime_s instead  
    printf( "Plus milliseconds:\t\t\t%u\n", tstruct.millitm );  
    printf( "Zone difference in hours from UTC:\t%u\n",   
             tstruct.timezone/60 );  
    printf( "Time zone name:\t\t\t\t%s\n", _tzname[0] ); //C4996  
    // Note: _tzname is deprecated; consider using _get_tzname  
    printf( "Daylight savings:\t\t\t%s\n",   
             tstruct.dstflag ? "YES" : "NO" );  
  
    // Make time for noon on Christmas, 1993.   
    if( mktime( &xmas ) != (time_t)-1 )  
    {  
       err = asctime_s(timebuf, 26, &xmas);  
       if (err)  
       {  
          printf("asctime_s failed due to an invalid argument.");  
          exit(1);  
       }  
       printf( "Christmas\t\t\t\t%s\n", timebuf );  
    }  
  
    // Use time structure to build a customized time string.   
    err = _localtime64_s( &today, &ltime );  
    if (err)  
    {  
        printf(" _localtime64_s failed due to invalid arguments.");  
        exit(1);  
    }  
  
    // Use strftime to build a customized time string.   
    strftime( tmpbuf, 128,  
         "Today is %A, day %d of %B in the year %Y.\n", &today );  
    printf( tmpbuf );  
}  
```  
  
```Output  
OS time:            13:51:23  
OS date:            04/25/03  
Time in seconds since UTC 1/1/70:   1051303883  
UNIX time and date:         Fri Apr 25 13:51:23 2003  
Coordinated universal time:      Fri Apr 25 20:51:23 2003  
12-hour time:            01:51:23 PM  
Plus milliseconds:         552  
Zone difference in hours from UTC:   8  
Time zone name:            Pacific Standard Time  
Daylight savings:         YES  
Christmas            Sat Dec 25 12:00:00 1993  
  
Today is Friday, day 25 of April in the year 2003.  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [asctime –, _wasctime –](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime_s –, _wasctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [_ftime – _ftime32 –, _ftime64 –](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime_s – _gmtime32_s –, _gmtime64_s –](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [místní čas, _localtime32 –, _localtime64 –](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [localtime_s – _localtime32_s –, _localtime64_s –](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [_utime –, _utime32 –, _utime64 –, _wutime –, _wutime32 –, _wutime64 –](../../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)