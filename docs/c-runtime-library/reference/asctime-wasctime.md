---
title: asctime, _wasctime
ms.date: 4/2/2020
api_name:
- _wasctime
- asctime
- _o__wasctime
- _o_asctime
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
ms.openlocfilehash: bda14f3b6046378ad23148371f354bb910163d3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350477"
---
# <a name="asctime-_wasctime"></a>asctime, _wasctime

Převeďte strukturu času **tm** na řetězec znaků. K dispozici jsou bezpečnější verze těchto funkcí. viz [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

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

**asctime** vrátí ukazatel na výsledek řetězce znaků; **_wasctime** vrátí ukazatel na výsledek řetězce s širokým znakem. Neexistuje žádná vrácená hodnota chyby.

## <a name="remarks"></a>Poznámky

K dispozici jsou bezpečnější verze těchto funkcí. viz [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

Funkce **asctime** převede čas uložený jako struktura na řetězec znaků. Hodnota *timeptr* je obvykle získána z volání **gmtime** nebo **localtime**, které oba vrátí ukazatel na strukturu **tm,** definovanou v TIME. H.

|člen timeptr|Hodnota|
|--------------------|-----------|
|**tm_hour**|Počet hodin od půlnoci (0-23)|
|**tm_isdst**|Pozitivní, pokud je v platnosti letní čas; 0, pokud letní čas není v platnosti; negativní, pokud není znám stav letního času. C run-time knihovna předpokládá pravidla Spojených států pro implementaci výpočtu letního času (DST).|
|**tm_mday**|Den v měsíci (1-31)|
|**tm_min**|Minuty po hodině (0-59)|
|**tm_mon**|Měsíc (0-11; Leden = 0)|
|**tm_sec**|Sekundpo minutě (0-59)|
|**tm_wday**|Den v týdnu (0-6; Neděle = 0)|
|**tm_yday**|Den v roce (0-365; 1. ledna = 0)|
|**tm_year**|Rok (aktuální rok minus 1900)|

Řetězec převedených znaků je také upraven podle nastavení místního časového pásma. Informace o konfiguraci místního času naleznete [v](time-time32-time64.md)tématech time , [_ftime](ftime-ftime32-ftime64.md)a [localtime](localtime-localtime32-localtime64.md) funkce a [_tzset](tzset.md) funkce informace o definování prostředí časového pásma a globálních proměnných.

Výsledek řetězce produkovaný **asctime** obsahuje přesně 26 znaků a má tvar `Wed Jan 02 02:03:55 1980\n\0`. Používá se 24hodinová hodina. Všechna pole mají konstantní šířku. Znak nového řádku a znak null zabírají poslední dvě pozice řetězce. **asctime** používá jednu staticky přidělenou vyrovnávací paměť k uložení návratového řetězce. Každé volání této funkce zničí výsledek předchozího volání.

**_wasctime** je širokoznaková verze **aplikace asctime**. **_wasctime** a **asctime** se chovají stejně jinak.

Tyto funkce ověřují jejich parametry. Pokud *timeptr* je ukazatel null nebo pokud obsahuje hodnoty mimo rozsah, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí **hodnotu NULL** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> \<nebo wchar.h>|

## <a name="example"></a>Příklad

Tento program umístí systémový čas do dlouhého **celého čísla aclock**, převede jej do struktury **newtime** a pak převede na řetězec formulář pro výstup, pomocí funkce **asctime.**

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

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
