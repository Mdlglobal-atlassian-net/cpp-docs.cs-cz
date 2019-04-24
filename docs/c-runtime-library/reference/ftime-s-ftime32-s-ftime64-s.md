---
title: _ftime_s, _ftime32_s, _ftime64_s
ms.date: 11/04/2016
apiname:
- _ftime_s
- _ftime64_s
- _ftime32_s
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
ms.openlocfilehash: 696b461cdb6b8d58bb668b996a99c5d0bb774d6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287678"
---
# <a name="ftimes-ftime32s-ftime64s"></a>_ftime_s, _ftime32_s, _ftime64_s

Získá aktuální čas. Jde o verzích [_ftime _ftime32, _ftime64](ftime-ftime32-ftime64.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Ukazatel **_timeb –**, **__timeb32**, nebo **__timeb64 –** struktury.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, při selhání kód chyby. Pokud *timeptr* je **NULL**, bude návratovou hodnotou **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Ftime_s** funkce získá aktuálním místním časem a uloží ho do struktury, na které odkazuje *timeptr*. **_Timeb –**, **__timeb32**, a **__timeb64 –** struktury jsou definovány v SYS\Timeb.h. Obsahují čtyři pole, které jsou uvedeny v následující tabulce.

|Pole|Popis|
|-|-|
|**dstflag**|Nenulové, pokud letní čas je aktuálně používána pro místní časové pásmo. (Viz [_tzset –](tzset.md) pro vysvětlení, jak se určují letní čas.)|
|**millitm**|Zlomek sekundy v milisekundách.|
|**čas**|Čas v řádu sekund od půlnoci (00: 00:00), 1. ledna 1970, koordinovaného univerzálního času (UTC).|
|**timezone**|Rozdíl v řádech minut, přesun westward, mezi místním časem a UTC. Hodnota **časové pásmo** nastavit hodnotu globální proměnné **_timezone** (viz **_tzset –**).|

**_Ftime64_s** funkci, která používá **__timeb64 –** struktury, umožňuje vytvoření souboru data vyjadřují až do 23:59:59, 31 prosince 3000 UTC, zatímco **_ftime32_s** pouze představuje data do 23:59:59 18. ledna 2038 UTC. Půlnoc 1. ledna 1970 je dolní mez rozsahu kalendářních dat pro všechny tyto funkce.

**_Ftime_s** funkce je ekvivalentní volání **_ftime64_s**, a **_timeb –** obsahuje čas 64-bit, není-li **_USE_32BIT_TIME_T** je definováno, v takovém případě staré chování je v platnosti; **_ftime_s** používá čas 32bitová verze a **_timeb –** obsahuje čas 32-bit.

**_ftime_s** ověří jeho parametry. Je-li předán ukazatel s hodnotou null jako *timeptr*, funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, funkce nastaví **errno** k **EINVAL**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_ftime_s**|\<SYS/Types.h > a \<sys/timeb.h >|
|**_ftime32_s**|\<SYS/Types.h > a \<sys/timeb.h >|
|**_ftime64_s**|\<SYS/Types.h > a \<sys/timeb.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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
