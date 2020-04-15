---
title: _tzset
ms.date: 4/2/2020
api_name:
- _tzset
- _o__tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: b2537a3bbfd2b5cec6bdf149c520aac7e3344b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362189"
---
# <a name="_tzset"></a>_tzset

Nastaví proměnné časového prostředí.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
void _tzset( void );
```

## <a name="remarks"></a>Poznámky

Funkce **_tzset** používá aktuální nastavení proměnné prostředí **TZ** k přiřazení hodnot třem globálním proměnným: **_daylight**, **_timezone**a **_tzname**. Tyto proměnné jsou používány [_ftime](ftime-ftime32-ftime64.md) a [místních](localtime-localtime32-localtime64.md) funkcí k provádění oprav z koordinovaného univerzálního času (UTC) na místní čas a [podle časové](time-time32-time64.md) funkce pro výpočet Času UTC ze systémového času. K nastavení proměnné prostředí **TZ** použijte následující syntaxi:

> **set TZ=**_tzn_ \[ **+**&#124;**-**]*hh*\[**:**_mm_\[**:**_ss_] ][*dzn*]

|Parametr|Popis|
|-|-|
| *tzn* | Název časového pásma se třemi písmeny, například PST. Je nutné zadat správný posun od místního času k času UTC. |
| *hh* | Rozdíl v hodinách mezi UTC a místním časem. Znaménko (+) volitelné pro kladné hodnoty. |
| *Mm* | Minut. Odděleny od *hh* tlustého střeva (**:**). |
| *Ss* | Sekund. Od *mm* odděleno dvojtečkou (**: .** |
| *dzn* | Třípísmenné časové pásmo pro úsporu letního času, například PDT. Pokud letní čas není nikdy v platnosti v lokalitě, nastavte **TZ** bez hodnoty pro *dzn*. C run-time knihovna předpokládá pravidla Spojených států pro implementaci výpočtu letního času (DST). |

> [!NOTE]
> Dávejte pozor při výpočtu znamení časového rozdílu. Vzhledem k tomu, že časový rozdíl je posun od místního času k UTC (spíše než naopak), jeho znaménko může být opakem toho, co můžete intuitivně očekávat. U časových pásem před časovou hodnotou UTC je časový rozdíl záporný. pro ty, kteří stojí za UTC, je rozdíl pozitivní.

Chcete-li například nastavit proměnnou prostředí **TZ** tak, aby odpovídala aktuálnímu časovému pásmu v Německu, zadejte na příkazovém řádku následující:

> **sada TZ=GST-1GDT**

Tento příkaz používá GST k označení německého standardního času, předpokládá, že Čas UTC je jednu hodinu za Německem (nebo jinými slovy, že Německo je o hodinu před UTC) a předpokládá, že Německo dodržuje letní čas.

Pokud hodnota **TZ** není nastavena, **_tzset** pokusí použít informace o časovém pásmu určené operačním systémem. V operačním systému Windows jsou tyto informace určeny v ovládacím panelu Datum a čas. Pokud **_tzset** nemůže získat tyto informace, používá PST8PDT ve výchozím nastavení, což znamená tichomořské časové pásmo.

Na základě hodnoty proměnné prostředí **TZ** jsou globálním proměnným přiřazeny **následující hodnoty, _daylight**, **_timezone**a **_tzname** při **volání _tzset:**

|Globální proměnná|Popis|Výchozí hodnota|
|---------------------|-----------------|-------------------|
|**_daylight**|Nenulová hodnota, pokud je v nastavení **TZ** zadáno časové pásmo pro úsporu letního času; jinak 0.|1|
|**_timezone**|Rozdíl v sekundách mezi místním časem a časem UTC.|28800 (28800 sekund se rovná 8 hodin)|
|**_tzname**[0]|Řetězcová hodnota názvu časového pásma z proměnné prostředí **TZ;** prázdné, pokud **tz** nebyla nastavena.|Pst|
|**_tzname**[1]|Řetězcová hodnota časového pásma pro úsporu letního času; prázdné, pokud je z proměnné prostředí **TZ** vynecháno letní časové pásmo.|Pdt|

Výchozí hodnoty zobrazené v předchozí tabulce pro **_daylight** a **_tzname** pole odpovídají "PST8PDT." Pokud je zóna letního času vynechána z proměnné prostředí **TZ,** hodnota **_daylight** je 0 a [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)a [localtime](localtime-localtime32-localtime64.md) funkce vrátí 0 pro jejich dst příznaky.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_tzset**|\<time.h>|

Funkce **_tzset** je specifické pro společnost Microsoft. Další informace naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
