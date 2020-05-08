---
title: gmtime, _gmtime32, _gmtime64
ms.date: 4/2/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: 16f4315837873c8d78065ea97a11188bdddedbed
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916242"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime, _gmtime32, _gmtime64

Převede hodnotu **time_t** času na strukturu **TM** . K dispozici jsou bezpečnější verze těchto funkcí; viz [gmtime_s, _gmtime32_s _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntaxe

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Ukazatel na uložený čas. Čas je vyjádřený jako sekund uplynulý od půlnoci (00:00:00), od 1. ledna 1970 a koordinovaného univerzálního času (UTC).

## <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu typu [TM](../../c-runtime-library/standard-types.md). Pole vrácené struktury uchovávají vyhodnocenou hodnotu argumentu *sourceTime* v čase UTC, nikoli v místním čase. Každé pole struktury je typu **int**, a to následujícím způsobem:

|Pole|Popis|
|-|-|
|**tm_sec**|Sekundy po minutě (0-59).|
|**tm_min**|Minut po hodině (0-59).|
|**tm_hour**|Hodiny od půlnoci (0-23).|
|**tm_mday**|Den v měsíci (1-31).|
|**tm_mon**|Měsíc (0-11; Leden = 0).|
|**tm_year**|Year (aktuální rok minus 1900).|
|**tm_wday**|Den v týdnu (0-6; Neděle = 0).|
|**tm_yday**|Den v roce (0-365; 1. ledna = 0).|
|**tm_isdst**|Vždy 0 pro **gmtime**.|

32 a 64 verze **gmtime**, [mktime](mktime-mktime32-mktime64.md), [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)a [localtime](localtime-localtime32-localtime64.md) používají pro převod jednu společnou strukturu **TM** na vlákno. Každé volání jedné z těchto funkcí zničí výsledek jakéhokoli předchozího volání. Pokud *sourceTime* představuje datum před půlnocí, 1. ledna 1970, **gmtime** vrátí **hodnotu null**. Nevrátila se žádná chybová zpráva.

**_gmtime64**, která používá strukturu **__time64_t** , umožňuje, aby data byla vyjádřena až 23:59:59, 31. prosince 3000, UTC, zatímco **_gmtime32** zastupují pouze data prostřednictvím 23:59:59 15. ledna, 2038, UTC. Půlnoc, 1. ledna 1970 je dolní mez rozsahu kalendářních dat obou funkcí.

**gmtime** je vložená funkce, která je vyhodnocena jako **_gmtime64**, a **time_t** je ekvivalentní **__time64_t** , pokud není definován **_USE_32BIT_TIME_T** . Pokud je nutné vynutit, aby kompilátor interpretoval **time_t** jako starou **time_t**32, můžete definovat **_USE_32BIT_TIME_T**, ale v takovém případě způsobí, že **gmtime** budou vloženy do **_gmtime32** a **time_t** budou definovány jako **__time32_t**. Doporučujeme, abyste to provedli, protože není povolená na 64ch platformách a v každém případě by vaše aplikace mohla selhat i po 18. lednu 2038.

Tyto funkce ověřují své parametry. Pokud je *sourceTime* ukazatel s hodnotou null, nebo pokud je hodnota *sourceTime* záporná, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **hodnotu null** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_gmtime32** rozdělí hodnotu *sourceTime* a uloží ji ve staticky přidělené struktuře typu **TM**, definované v čase. Y. Hodnota *sourceTime* je obvykle získána voláním funkce [Time](time-time32-time64.md) .

> [!NOTE]
> Ve většině případů se cílové prostředí pokusí zjistit, jestli je v platnosti letní čas. Knihovna run-time jazyka C předpokládá, že jsou použita pravidla USA pro implementaci výpočtu letního času (DST).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Povinné záhlaví jazyka C|Požadovaná hlavička C++|
|-------------|---------------------|-|
|**gmtime**, **_gmtime32** **_gmtime64**|\<Time. h>|\<CTime –> nebo \<Time. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
