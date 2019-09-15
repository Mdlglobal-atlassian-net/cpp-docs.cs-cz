---
title: _tzset
ms.date: 11/04/2016
api_name:
- _tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: e9ea454ede370a20779b5852b426b418db81757c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957552"
---
# <a name="_tzset"></a>_tzset

Nastaví proměnné prostředí času.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
void _tzset( void );
```

## <a name="remarks"></a>Poznámky

Funkce **_tzset** používá aktuální nastavení proměnné prostředí **TZ** k přiřazení hodnot třem globálním proměnným: **_daylight**, **_timezone**a **_tzname**. Tyto proměnné jsou používány funkcemi [_ftime](ftime-ftime32-ftime64.md) a [localtime](localtime-localtime32-localtime64.md) k provádění oprav z koordinovaného univerzálního času (UTC) po místní čas a podle [časové](time-time32-time64.md) funkce pro výpočet času UTC ze systémového času. Pomocí následující syntaxe nastavte proměnnou prostředí **TZ** :

> **nastavit TZ =** _tzn_ &#124;]HH\[:mm\[: SS]] [dzn] \[ **+** **-**

|Parametr|Popis|
|-|-|
| *tzn* | Tři dopisy: název časové zóny, například PST. Je nutné zadat správný posun z místního času na čas UTC. |
| *hh* | Rozdíl v hodinách mezi časem UTC a místním časem. Znaménko (+) volitelné pro kladné hodnoty. |
| *mm* | Minuty. Oddělené od *HH* dvojtečkou ( **:** ). |
| *ss* | Second. Oddělené od *mm* dvojtečkou ( **:** ). |
| *dzn* | Tři písmena při letním čase, například PDT. Pokud se letní čas v tomto případě nikdy neprojeví v rámečku, nastavte hodnotu **TZ** bez hodnoty pro *dzn*. Knihovna run-time jazyka C předpokládá pravidla USA pro implementaci výpočtu letního času (DST). |

> [!NOTE]
> Při výpočtu časového rozdílu se ujistěte, že se liší. Vzhledem k tomu, že časový rozdíl je posun od místního času k času UTC (místo opačného), jeho znaménko může být opakem toho, co byste mohli intuitivní očekávat. Pro časová pásma před časem UTC je časový rozdíl záporný. u těch za časem UTC je rozdíl kladný.

Chcete-li například nastavit proměnnou prostředí **TZ** tak, aby odpovídala aktuálnímu časovému pásmu v Německu, zadejte na příkazovém řádku následující příkaz:

> **set TZ=GST-1GDT**

Tento příkaz používá daň GST k označení německého standardního času, předpokládá, že UTC je jedna hodina za Německem (nebo jinými slovy, že Německo je jedna hodina před časem UTC) a předpokládá, že Německo sleduje letní čas.

Pokud není nastavená hodnota **TZ** , **_tzset** se pokusí použít informace o časovém pásmu určené operačním systémem. V operačním systému Windows jsou tyto informace uvedeny v aplikaci datum/čas v Ovládacích panelech. Pokud **_tzset** nemůže získat tyto informace, použije PST8PDT ve výchozím nastavení, což znamená časové pásmo tichomořského.

Na základě hodnoty proměnné prostředí **TZ** jsou k globálním proměnným **_daylight**, **_timezone**a **_tzname** při volání **_tzset** přiřazeny následující hodnoty:

|Globální proměnná|Popis|Výchozí hodnota|
|---------------------|-----------------|-------------------|
|**_daylight**|Nenulová hodnota, pokud je v nastavení **TZ** zadáno časové pásmo letního času; v opačném případě 0.|1|
|**_timezone**|Rozdíl v sekundách mezi místním časem a UTC.|28800 (28800 sekund se rovná 8 hodin)|
|**_tzname** 0,8|Řetězcová hodnota názvu časového pásma z části **TZ** prostředí – proměnná; prázdné, pokud nebylo nastaveno na hodnotu **TZ** .|VYTVOŘENÉ|
|**_tzname**[1]|Hodnota řetězce v časovém pásmu letního času; prázdné, pokud je v časovém pásmu **TZ** z pohyblivé proměnné prostředí vynecháno letní čas.|PDT|

Výchozí hodnoty uvedené v předchozí tabulce pro **_daylight** a pole **_TZNAME** odpovídají "PST8PDT." Pokud je zóna letního času vynechána z proměnné prostředí **TZ** , hodnota **_daylight** je 0 a funkce [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)a [localtime](localtime-localtime32-localtime64.md) vrátí hodnotu 0 pro své příznaky letního času.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_tzset**|\<time.h>|

Funkce **_tzset** je specifická pro společnost Microsoft. Další informace najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_tzset.cpp
// This program uses _tzset to set the global variables
// named _daylight, _timezone, and _tzname. Since TZ is
// not being explicitly set, it uses the system time.

#include <time.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    _tzset();
    int daylight;
    _get_daylight( &daylight );
    printf( "_daylight = %d\n", daylight );
    long timezone;
    _get_timezone( &timezone );
    printf( "_timezone = %ld\n", timezone );
    size_t s;
    char tzname[100];
    _get_tzname( &s, tzname, sizeof(tzname), 0 );
    printf( "_tzname[0] = %s\n", tzname );
    exit( 0 );
}
```

```Output
_daylight = 1
_timezone = 28800
_tzname[0] = Pacific Standard Time
```

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
