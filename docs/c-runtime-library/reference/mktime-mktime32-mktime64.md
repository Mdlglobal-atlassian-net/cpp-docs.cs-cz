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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 48d1104d9680fe8ab88f0f73bfc179f3e4cf45a6
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919072"
---
# <a name="mktime-_mktime32-_mktime64"></a>mktime, _mktime32, _mktime64

Převede místní čas na hodnotu kalendáře.

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
Ukazatel na časovou strukturu; viz [asctime](asctime-wasctime.md).

## <a name="return-value"></a>Návratová hodnota

**_mktime32** vrátí zadaný čas kalendáře kódovaný jako hodnota typu [time_t](../../c-runtime-library/standard-types.md). Pokud *timeptr* odkazuje na datum před půlnocí, 1. ledna 1970, nebo pokud čas kalendáře nelze znázornit, **_mktime32** vrátí **time_t**typu přetypování-1. Při použití **_mktime32** a pokud *timeptr* odkazuje na datum po 23:59:59 18. ledna 2038, KOORDINOVANÝ světový čas (UTC), vrátí-1 přetypování na typ **time_t**.

**_mktime64** vrátí hodnotu-1 přetypování na typ **__time64_t** , pokud *timeptr* odkazuje na datum po 23:59:59, 31. prosince 3000, UTC.

## <a name="remarks"></a>Poznámky

Funkce **mktime**, **_mktime32** a **_mktime64** převádějí poskytnutou časovou strukturu (možná nekompletní), na kterou odkazuje *timeptr* do plně definované struktury s normalizovanými hodnotami a následně je převede na hodnotu **time_t** kalendářního času. Převedený čas má stejné kódování jako hodnoty vrácené funkcí [Time](time-time32-time64.md) . Původní hodnoty **tm_wday** a **tm_yday** komponent struktury *timeptr* jsou ignorovány a původní hodnoty ostatních komponent nejsou omezeny na jejich normální rozsahy.

**mktime** je vložená funkce, která je ekvivalentní **_mktime64**, pokud není definována **_USE_32BIT_TIME_T** , v takovém případě je ekvivalentem **_mktime32**.

Po úpravě na čas UTC **_mktime32** zpracovává data od půlnoci 1. ledna 1970 do 23:59:59. ledna, 2038, UTC. **_mktime64** zpracovává data od půlnoci 1. ledna 1970 do 23:59:59, 31. prosince 3000. Tato úprava může způsobit, že tyto funkce vrátí hodnotu-1 (přetypování do **time_t**, **__time32_t** nebo **__time64_t**), i když zadané datum spadá do rozsahu. Například pokud jste v Cairo, Egyptě, což je dvě hodiny před časem UTC, dvě hodiny se nejprve odečtou od data, které zadáte v *timeptr*. nyní může být datum mimo rozsah.

Tyto funkce se dají použít k ověření a vyplnění struktury TM. V případě úspěchu tyto funkce nastavují hodnoty **tm_wday** a **tm_yday** podle potřeby a nastavují ostatní komponenty tak, aby představovaly zadaný čas kalendáře, ale jejich hodnoty jsou vynucené do normálního rozsahu. Konečná hodnota **tm_mday** není nastavena, dokud nejsou určeny **tm_mon** a **tm_year** . Při určování doby struktury **TM** nastavte pole **tm_isdst** na:

- Nula (0) pro indikaci, že standardní čas je platný.

- Hodnota větší než 0 značící, že je platný letní čas.

- Hodnota menší než nula znamená, že kód běhové knihovny jazyka C bude počítat bez ohledu na to, zda platí standardní čas nebo letní čas.

Knihovna run-time jazyka C určí chování letního času z proměnné prostředí [TZ](tzset.md) . Pokud není nastavená oblast **TZ** , Win32 API volání [GetTimeZoneInformation](/windows/win32/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) slouží k získání informací o letním čase z operačního systému. Pokud se to nepovede, knihovna předpokládá, že se použijí pravidla USA pro implementaci výpočtu letního času. **tm_isdst** je povinné pole. Pokud není nastavena, jeho hodnota je nedefinovaná a návratová hodnota z těchto funkcí je nepředvídatelné. Pokud *timeptr* odkazuje na strukturu **TM** , kterou vrátilo předchozí volání [asctime](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md)nebo [localtime](localtime-localtime32-localtime64.md) (nebo varianty těchto funkcí), pole **tm_isdst** obsahuje správnou hodnotu.

Všimněte si, že **gmtime** a **localtime** (a **_gmtime32**, **_gmtime64**, **_localtime32**a **_localtime64**) používají pro převod jednu vyrovnávací paměť na vlákno. Pokud zadáte tuto vyrovnávací paměť pro **mktime**, **_mktime32** nebo **_mktime64**, bude předchozí obsah zničen.

Tyto funkce ověřují svůj parametr. Pokud je *timeptr* ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mktime**|\<Time. h>|
|**_mktime32**|\<Time. h>|
|**_mktime64**|\<Time. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

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
