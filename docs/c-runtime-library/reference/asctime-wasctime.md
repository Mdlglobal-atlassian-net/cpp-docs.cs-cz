---
title: asctime, _wasctime
ms.date: 11/04/2016
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
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: bc2d7a50442d9000eaaebf7a06bf336b3317e4df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577895"
---
# <a name="asctime-wasctime"></a>asctime, _wasctime

Převést **tm** čas struktury na řetězec znaků. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [asctime_s, _wasctime_s – –](asctime-s-wasctime-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>Parametry

*timeptr*<br/>
Struktura času a data.

## <a name="return-value"></a>Návratová hodnota

**asctime –** vrací ukazatel na výsledek řetězce znak; **_wasctime –** vrací ukazatel na výsledek řetězce širokého znaku. Neexistuje žádná návratová hodnota chyba.

## <a name="remarks"></a>Poznámky

Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [asctime_s, _wasctime_s – –](asctime-s-wasctime-s.md).

**Asctime –** funkce převede čas uložené jako struktury na řetězec znaků. *Timeptr* hodnota se obvykle získá z volání **gmtime** nebo **localtime**, které vracejí ukazatele na **tm** strukturu, definované v čase. H.

|člen timeptr|Hodnota|
|--------------------|-----------|
|**tm_hour**|Hodiny od půlnoci (0-23)|
|**tm_isdst**|Kladná, pokud je v platnosti; letního času 0, pokud není platná; letního času záporná, pokud stav letní čas není znám. Knihovny run-time jazyka C předpokládá použita pravidla Spojených států pro implementaci výpočtu letního času (DST).|
|**tm_mday**|Den v měsíci (1-31)|
|**tm_min**|Minuty po hodině (0 – 59)|
|**tm_mon**|Měsíc (0 – 11; Leden = 0)|
|**tm_sec**|Sekundy po minutě (0 – 59)|
|**tm_wday**|Den v týdnu (0 – 6; Neděle = 0)|
|**tm_yday**|Den roku (0-365; 1. ledna = 0)|
|**tm_year**|Rok (aktuální rok minus 1900)|

Řetězec převedený znak je také upravena podle nastavení místní časové pásmo. Informace o konfiguraci místního času, najdete v článku [čas](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), a [localtime](localtime-localtime32-localtime64.md) funkce a [_tzset –](tzset.md) – funkce informace o definování prostředí časové pásmo a globální proměnné.

Řetězec výsledek produkovaný **asctime –** obsahuje přesně 26 znaků a má tvar `Wed Jan 02 02:03:55 1980\n\0`. Se používá 24hodinový formát. Všechna pole mají konstantní šířce. Znak nového řádku a znak null zabírat posledních dvou pozic řetězce. **asctime –** používá jeden staticky přidělenou vyrovnávací paměť pro vrácený řetězec. Každé volání funkcí ničí výsledek předchozího volání.

**_wasctime –** je verze širokého znaku **asctime –**. **_wasctime –** a **asctime –** se jinak chovají stejně.

Tyto funkce ověřují své parametry. Pokud *timeptr* je ukazatel s hodnotou null, nebo pokud obsahuje hodnoty mimo rozsah, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **NULL** a nastaví **errno** k **EINVAL**.

### <a name="generic-text-routine-mapping"></a>Rutiny mapování obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime –**|**asctime –**|**asctime –**|**_wasctime**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**asctime –**|\<Time.h >|
|**_wasctime**|\<Time.h > nebo \<wchar.h >|

## <a name="example"></a>Příklad

Tento program umístí systémový čas dlouhé celé číslo **aclock**, přeloží ho do struktury **newtime** a poté převádí řetězec formuláře pro výstup, pomocí **asctime –** funkce.

```C
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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
