---
title: mktime, _mktime32, _mktime64
ms.date: 11/04/2016
apiname:
- _mktime32
- mktime
- _mktime64
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
ms.openlocfilehash: 8e9524249d6c90323bdcfc0b92ecf2dad281c79b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499902"
---
# <a name="mktime-mktime32-mktime64"></a>mktime, _mktime32, _mktime64

Místní čas převeďte na hodnotu kalendáře.

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
Ukazatel na strukturu čas; Zobrazit [asctime –](asctime-wasctime.md).

## <a name="return-value"></a>Návratová hodnota

**_mktime32** vrací čas zadaný kalendář zakódován jako hodnotu typu [time_t](../../c-runtime-library/standard-types.md). Pokud *timeptr* odkazuje na datum před půlnocí, 1. ledna 1970, nebo pokud nemůže být reprezentovaná času v kalendáři, **_mktime32** vrátí hodnotu -1 přetypován na typ **time_t**. Při použití **_mktime32** a pokud *timeptr* odkazuje na data po 23:59:59 18. ledna 2038 koordinovaný univerzální čas (UTC), vrátí hodnotu -1 přetypován na typ **time_t**.

**_mktime64** vrátí -1 přetypován na typ **__time64_t –** Pokud *timeptr* odkazuje na data po 23:59:59, 31 prosince 3000 UTC.

## <a name="remarks"></a>Poznámky

**Mktime**, **_mktime32** a **_mktime64** převádějí (pravděpodobně neúplný) zadaný čas struktura odkazované *timeptr*do plně definovaná struktury s normalizované hodnoty a potom převede **time_t** hodnotu času v kalendáři. Převedený čas má stejné kódování jako hodnot vrácených [čas](time-time32-time64.md) funkce. Původní hodnoty **tm_wday** a **tm_yday** komponenty *timeptr* struktury jsou ignorovány a původní hodnoty ostatní součásti nejsou s omezeným přístupem do svého normálního rozsahu.

**mktime** je vložená funkce, která je ekvivalentní **_mktime64**, není-li **_USE_32BIT_TIME_T** je definován v takovém případě je ekvivalentní **_mktime32** .

Po úpravě na čas UTC **_mktime32** zpracovává data od půlnoci 1. ledna 1970, do 23:59:59 18. ledna 2038 UTC. **_mktime64** zpracovává data od půlnoci 1. ledna 1970 do 23:59:59, 31 prosince 3000. Toto nastavení může způsobit, že tyto funkce k vrátí hodnotu -1 (přetypovat na **time_t**, **__time32_t** nebo **__time64_t –**) i v případě, že zadáte datum je v rozsahu. Například pokud jste v Káhira, Egypt, která je dvě hodiny před časem UTC, dvě hodiny se nejprve bude odečítat od zadáte datum *timeptr*; to teď může vložit vaše data mimo rozsah.

Tyto funkce slouží k ověření a vyplňte strukturu tm. Pokud úspěšné, tyto funkce nastaví hodnoty **tm_wday** a **tm_yday** podle potřeby a nastavit další součásti představují čas zadaný kalendář, ale jejich hodnotami vynucené na normální rozsahy. Konečná hodnota **tm_mday** není nastavena do **tm_mon** a **tm_year** jsou určeny. Při zadávání **tm** struktury čas, nastavte **tm_isdst** pole:

- Nula (0) k označení, že je v platnosti (běžný čas).

- Hodnota, která je větší než 0, která znamená, že je v platnosti letní čas.

- Hodnotu menší než nula, která mají kód knihovny run-time C compute, zda (běžný čas) nebo letního času je v platnosti.

Určuje chování letního času úspory času z knihovny run-time jazyka C [TZ](tzset.md) proměnné prostředí. Pokud **TZ** není nastavena, voláním rozhraní Win32 API [funkce GetTimeZoneInformation](/windows/desktop/api/timezoneapi/nf-timezoneapi-gettimezoneinformation) slouží k získání letní čas informace z operačního systému. Když se to nepovede, knihovně předpokládá, že jsou použita pravidla Spojených států pro implementaci výpočtu letního času. **tm_isdst** je povinné pole. Pokud není nastavena, její hodnota není definována a návratovou hodnotu z těchto funkcí nepředvídatelné. Pokud *timeptr* odkazuje na **tm** struktura vrácený z předchozího volání [asctime –](asctime-wasctime.md), [gmtime](gmtime-gmtime32-gmtime64.md), nebo [localtime](localtime-localtime32-localtime64.md) (nebo varianty těchto funkcí), **tm_isdst** pole obsahuje správnou hodnotu.

Všimněte si, že **gmtime** a **localtime** (a **_gmtime32**, **_gmtime64**, **_localtime32**, a **_localtime64**) použijte jednu vyrovnávací paměť na vlákno pro převod. Pokud zadáte tuto vyrovnávací paměť pro **mktime**, **_mktime32** nebo **_mktime64**, předchozí obsah je zničen.

Tyto funkce ověřují své parametru. Pokud *timeptr* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, vrátí funkce hodnotu -1 a nastaví **errno** k **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mktime**|\<Time.h >|
|**_mktime32**|\<Time.h >|
|**_mktime64**|\<Time.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime, _mkgmtime32, _mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
