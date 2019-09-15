---
title: asctime, _wasctime
ms.date: 11/04/2016
api_name:
- _wasctime
- asctime
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
ms.openlocfilehash: 9ca9bbcbfff3d2bef41443ff1744a1b612727c20
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939671"
---
# <a name="asctime-_wasctime"></a>asctime, _wasctime

Převést časovou strukturu **správce** na řetězec znaků. K dispozici jsou bezpečnější verze těchto funkcí; viz [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

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
Struktura data a času.

## <a name="return-value"></a>Návratová hodnota

**asctime** vrací ukazatel na výsledek řetězce znaků; **_wasctime** vrací ukazatel na výsledek řetězce s velkým znakem. Nechybí návratová hodnota.

## <a name="remarks"></a>Poznámky

K dispozici jsou bezpečnější verze těchto funkcí; viz [asctime_s, _wasctime_s](asctime-s-wasctime-s.md).

Funkce **asctime** převede čas uložený jako strukturu na řetězec znaků. Hodnota *timeptr* je obvykle získána ze volání **gmtime** nebo **localtime**, který vrací ukazatel na strukturu **TM** definovanou v čase. Y.

|člen timeptr|Value|
|--------------------|-----------|
|**tm_hour**|Hodiny od půlnoci (0-23)|
|**tm_isdst**|Kladné, pokud je v platnosti letní čas; 0, pokud letní čas neplatí; záporné, pokud stav letního času není známý. Knihovna run-time jazyka C předpokládá pravidla USA pro implementaci výpočtu letního času (DST).|
|**tm_mday**|Den v měsíci (1-31)|
|**tm_min**|Minuty po hodině (0-59)|
|**tm_mon**|Měsíc (0-11; Leden = 0)|
|**tm_sec**|Sekundy po minutě (0-59)|
|**tm_wday**|Den v týdnu (0-6; Neděle = 0)|
|**tm_yday**|Den v roce (0-365; 1. ledna = 0)|
|**tm_year**|Year (aktuální rok minus 1900)|

Převedený řetězec znaků je také upraven podle nastavení místního časového pásma. Informace o konfiguraci místního času naleznete v tématu funkce [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)a [localtime](localtime-localtime32-localtime64.md) a funkce [_tzset](tzset.md) pro informace o definování prostředí časového pásma a globálních proměnných.

Výsledek řetězce vytvořený pomocí **asctime** obsahuje přesně 26 znaků a má formu `Wed Jan 02 02:03:55 1980\n\0`. Použije se 24hodinový čas. Všechna pole mají konstantní šířku. Znak nového řádku a znak null zabírají poslední dvě pozice řetězce. **asctime** používá pro uložení návratového řetězce jednu staticky přidělenou vyrovnávací paměť. Každé volání této funkce zničí výsledek předchozího volání.

**_wasctime** je verze **asctime**s velkým znakem. **_wasctime** a **asctime** se chovají stejně jinak.

Tyto funkce ověřují své parametry. Pokud je *timeptr* ukazatel s hodnotou null, nebo pokud obsahuje hodnoty mimo rozsah, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce **hodnotu null** a nastaví **errno** na **EINVAL**.

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<Time. h > nebo \<WCHAR. h >|

## <a name="example"></a>Příklad

Tento program umístí systémový čas do dlouhého celého čísla **ACLOCK**, převede ho do struktury **newtime** a pak ji převede na formát řetězce pro výstup pomocí funkce **asctime** .

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
