---
title: _ftime_s, _ftime32_s, _ftime64_s
ms.date: 11/04/2016
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
ms.openlocfilehash: b45a22afc824a33e81170f954e6f99088b629f83
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956329"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s, _ftime32_s, _ftime64_s

Získá aktuální čas. Jedná se o verze [_ftime, _ftime32 a _ftime64](ftime-ftime32-ftime64.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Ukazatel na strukturu **_timeb**, **__timeb32**nebo **__timeb64** .

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, chybový kód při selhání. Pokud má timeptr **hodnotu null**, návratová hodnota je **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_ftime_s** získá aktuální místní čas a uloží ji do struktury, na kterou odkazuje *timeptr*. Struktury **_timeb**, **__timeb32**a **__timeb64** jsou definované v SYS\Timeb.h. Obsahují čtyři pole, která jsou uvedena v následující tabulce.

|Pole|Popis|
|-|-|
|**dstflag**|Nenulové, pokud je letní čas v současnosti platný pro místní časové pásmo. (Viz [_tzset](tzset.md) pro vysvětlení, jak se určuje letní čas.)|
|**millitm**|Zlomek sekundy v milisekundách.|
|**čas**|Čas v sekundách od půlnoci (00:00:00), 1. ledna 1970, koordinovaný světový čas (UTC).|
|**údaj**|Rozdíl v minutách, pohybování Westward, mezi časem UTC a místním časem. Hodnota **časového pásma** je nastavena z hodnoty globální proměnné **_timezone** (viz **_tzset**).|

Funkce **_ftime64_s** , která používá strukturu **__timeb64** , umožňuje, aby data vytváření souborů byla vyjádřena až 23:59:59, 31. prosince 3000, UTC; zatímco **_ftime32_s** představuje pouze kalendářní data 23:59:59 do 18. ledna 2038, UTC. Půlnoc, 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

Funkce **_ftime_s** je ekvivalentem **_ftime64_s**a **_timeb** obsahuje 64, pokud není definována **_USE_32BIT_TIME_T** , v takovém případě se stará chování projeví. **_ftime_s** používá 32ový čas a **_timeb** obsahuje 32-bit času.

**_ftime_s** ověří své parametry. Pokud byl předán ukazatel s hodnotou null jako *timeptr*, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce nastaví **errno** na **EINVAL**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_ftime_s**|\<sys/Types. h > \<a sys/timeb. h >|
|**_ftime32_s**|\<sys/Types. h > \<a sys/timeb. h >|
|**_ftime64_s**|\<sys/Types. h > \<a sys/timeb. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_ftime64_s.c
// This program uses _ftime64_s to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime64_s( &timebuffer );

    time1 = timebuffer.time;
    millitm1 = timebuffer.millitm;
    timezone1 = timebuffer.timezone;
    dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
