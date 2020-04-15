---
title: _ftime_s, _ftime32_s, _ftime64_s
ms.date: 4/2/2020
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
- _o__ftime32_s
- _o__ftime64_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0ffd779d8c74b64403837bd973b025da7e3fac2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345555"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s, _ftime32_s, _ftime64_s

Získá aktuální čas. Jedná se o verze [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) s vylepšeními zabezpečení popsanými v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Ukazatel na **strukturu _timeb**, **__timeb32**nebo **__timeb64.**

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání. Pokud *je hodnota null,* vrácená hodnota je **EINVAL**. **NULL**

## <a name="remarks"></a>Poznámky

Funkce **_ftime_s** získá aktuální místní čas a uloží jej do struktury, na kterou se vztahuje *timeptr*. Struktury **_timeb**, **__timeb32**a **__timeb64** jsou definovány v souborech SYS\Timeb.h. Obsahují čtyři pole, která jsou uvedena v následující tabulce.

|Pole|Popis|
|-|-|
|**dstflag**|Nenulová, pokud letní čas je aktuálně v platnosti pro místní časové pásmo. (Vysvětlení, jak je určen letní čas, naleznete [_tzset.)](tzset.md)|
|**mlýnek**|Zlomek sekundy v milisekundách.|
|**Čas**|Čas v sekundách od půlnoci (00:00:00), 1.|
|**Timezone**|Rozdíl v minutách, pohybující se na západ, mezi UTC a místním časem. Hodnota **časového pásma** je nastavena z hodnoty globální proměnné **_timezone** (viz **_tzset**).|

Funkce **_ftime64_s,** která používá **__timeb64** strukturu, umožňuje vyjádřit data vytvoření souboru až do 23:59:59, prosinec 31, 3000, UTC; vzhledem k **tomu, _ftime32_s** představuje pouze data do 23:59:59 Leden 18, 2038, UTC. Půlnoc 1. ledna 1970 je dolní mez časového období pro všechny tyto funkce.

Funkce **_ftime_s** je ekvivalentní **_ftime64_s**a **_timeb** obsahuje 64bitový čas, pokud není **definována _USE_32BIT_TIME_T,** v takovém případě je staré chování v platnosti; **_ftime_s** používá 32bitový čas a **_timeb** obsahuje 32bitový čas.

**_ftime_s** ověří jeho parametry. Pokud je předán ukazatel null jako *timeptr*, funkce vyvolá neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> \<a sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> \<a sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> \<a sys/timeb.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
