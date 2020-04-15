---
title: mktime, _mktime32, _mktime64
ms.date: 4/2/2020
api_name:
- _mktime32
- mktime
- _mktime64
- _o__mktime32
- _o__mktime64
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
- mktime
- _mktime64
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
ms.openlocfilehash: b0981f33d70945083eacd28eb7517e80b3f2539f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338706"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime, _mktime32, _mktime64

Převeďte místní čas na hodnotu kalendáře.

## <a name="syntax"></a>Syntaxe

```C
time_t mktime(
   struct tm *timeptr
);
__time32_t _mktime32(
   struct tm *timeptr
);
__time64_t _mktime64(
   struct tm *timeptr
);
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Ukazatel na strukturu času; viz [asctime](asctime-wasctime.md).

## <a name="return-value"></a>Návratová hodnota

**_mktime32** vrátí zadaný čas kalendáře kódovaný jako hodnota typu [time_t](../../c-runtime-library/standard-types.md). Pokud *timeptr* odkazuje na datum před půlnocí, **time_t** **_mktime32** 1. Při použití **_mktime32** a pokud *timeptr* odkazuje na datum po 23:59:59 Leden 18, 2038, Koordinovaný světový čas (UTC), vrátí -1 přetypování typu **time_t**.

**_mktime64** vrátí -1 obsazení typu **__time64_t** pokud *timeptr* odkazuje na datum po 23:59:59, prosinec 31, 3000, UTC.

## <a name="remarks"></a>Poznámky

**Funkce mktime**, **_mktime32** a **_mktime64** převedou zadanou časovou strukturu (případně neúplnou) na kterou je uvedeno *timeptr* na plně definovanou strukturu s normalizovanými hodnotami a poté ji převede na **time_t** kalendářní ho času. Převedený čas má stejné kódování jako hodnoty vrácené [funkcí time.](time-time32-time64.md) Původní hodnoty **tm_wday** a **tm_yday** součásti struktury *timeptr* jsou ignorovány a původní hodnoty ostatních součástí nejsou omezeny na jejich normální rozsahy.

**mktime** je vřadná funkce, která je ekvivalentní **_mktime64**, pokud není **definována _USE_32BIT_TIME_T,** v takovém případě je ekvivalentní **_mktime32**.

Po úpravě UTC, **_mktime32** zpracovává data od půlnoci, leden 1, 1970, do 23:59:59 Leden 18, 2038, UTC. **_mktime64** zpracovává data od půlnoci, leden 1, 1970 do 23:59:59, Prosinec 31, 3000. Toto nastavení může způsobit, že tyto funkce vrátí -1 (přetypování do **time_t**, **__time32_t** nebo **__time64_t**) i v případě, že zadané datum je v dosahu. Pokud se například nacházíte v Káhiře v Egyptě, což je dvě hodiny před časem UTC, budou nejprve odečteny dvě hodiny od data, které zadáte v *poli timeptr*; to může nyní dát vaše data mimo rozsah.

Tyto funkce mohou být použity k ověření a vyplnění struktury tm. Pokud jsou tyto funkce úspěšné, nastaví hodnoty **tm_wday** a **tm_yday** podle potřeby a ostatní součásti představují zadaný kalendář, ale jejich hodnoty jsou vynuceny normálním rozsahem. Konečná hodnota **tm_mday** není nastavena, dokud **tm_mon** a **tm_year** nejsou určeny. Při určování času struktury **tm** nastavte **pole tm_isdst** na:

- Nula (0) označuje, že standardní čas je v platnosti.

- Hodnota větší než 0 označuje, že letní čas je v platnosti.

- Hodnota menší než nula, aby kód knihovny c run-time vypočítal, zda je v platnosti standardní čas nebo letní čas.

C run-time knihovna určí letní čas chování z proměnné prostředí [TZ.](tzset.md) Pokud **TZ** není nastavena, Win32 API volání [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) se používá k získání informací o letním čase z operačního systému. Pokud se to nezdaří, knihovna předpokládá, že jsou použita pravidla Spojených států pro implementaci výpočtu letního času. **tm_isdst** je povinné pole. Pokud není nastavena, jeho hodnota není definována a vrácená hodnota z těchto funkcí je nepředvídatelná. Pokud *timeptr* odkazuje na strukturu **tm** vrácenou předchozím voláním [na asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)nebo [localtime](localtime-localtime32-localtime64.md) (nebo varianty těchto funkcí), **obsahuje tm_isdst** pole správnou hodnotu.

Všimněte si, že **gmtime** a **místní čas** (a **_gmtime32**, **_gmtime64**, **_localtime32**a **_localtime64**) použít jednu vyrovnávací paměť na vlákno pro převod. Pokud zadáte tuto vyrovnávací paměť **mktime**, **_mktime32** nebo **_mktime64**, předchozí obsah bude zničen.

Tyto funkce ověřují jejich parametr. Pokud *timeptr* je nula ukazatel, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí -1 a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mktime**|\<time.h>|
|**_mktime32**|\<time.h>|
|**_mktime64**|\<time.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven c run-time](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_mktime.c
/* The example takes a number of days
* as input and returns the time, the current
* date, and the specified number of days.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm  when;
   __time64_t now, result;
   int        days;
   char       buff[80];

   time( &now );
   _localtime64_s( &when, &now );
   asctime_s( buff, sizeof(buff), &when );
   printf( "Current time is %s\n", buff );
   days = 20;
   when.tm_mday = when.tm_mday + days;
   if( (result = mktime( &when )) != (time_t)-1 ) {
      asctime_s( buff, sizeof(buff), &when );
      printf( "In %d days the time will be %s\n", days, buff );
   } else
      perror( "mktime failed" );
}
```

### <a name="sample-output"></a>Vzorový výstup

```Output
Current time is Fri Apr 25 13:34:07 2003

In 20 days the time will be Thu May 15 13:34:07 2003
```

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
