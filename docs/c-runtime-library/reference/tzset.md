---
title: _tzset
ms.date: 11/04/2016
apiname:
- _tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: 6312297e6daa9b4790674bd26d21812d5bee34c6
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330252"
---
# <a name="tzset"></a>_tzset

Nastavujte časové proměnné prostředí.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
void _tzset( void );
```

## <a name="remarks"></a>Poznámky

**_Tzset –** funkce používá aktuální nastavení proměnné prostředí **TZ** k přiřazení hodnot ke třem globálním proměnným: **_daylight**, **_timezone** , a **_tzname**. Tyto proměnné jsou používány [_ftime](ftime-ftime32-ftime64.md) a [localtime](localtime-localtime32-localtime64.md) funkce a opravte od koordinovaného univerzálního času (UTC) k místním čase a [čas](time-time32-time64.md) funkce vypočítání UTC ze systémového času. Použijte následující syntax k nastavení **TZ** proměnné prostředí:

> **Nastavte TZ =**_tzn_ \[ **+** &#124; **-**]*hh* \[ **:**_mm_\[**:**_ss_]] [*dzn*]

|Parametr|Popis|
|-|-|
| *tzn* | Třípísmenný název časového pásma, například PST. Je nutné zadat správný posun od místního času na čas UTC. |
| *hh* | Rozdíl v hodinách mezi místním časem a UTC. Znaménko (+) pro kladné hodnoty volitelné. |
| *mm* | Minut. Oddělená od *hh* dvojtečkou (**:**). |
| *ss* | Sekundy. Oddělená od *mm* dvojtečkou (**:**). |
| *dzn* | Zóna letního času tří písmen jako je například PDT. Pokud letní čas nepoužívá v oblasti, nastavit **TZ** bez hodnoty pro *dzn*. Knihovny run-time jazyka C předpokládá použita pravidla Spojených států pro implementaci výpočtu letního času (DST). |

> [!NOTE]
> Dejte si pozor při výpočtu znaménka časového rozdílu. Protože časový rozdíl je posun od místního času na čas UTC (spíše než naopak), jeho znaménko může být opakem toho, co intuitivně očekáváte. Pro časová pásma před časem UTC je časový rozdíl záporný; pro ta za UTC je rozdíl kladný.

Chcete-li například nastavit **TZ** proměnnou prostředí tak, aby odpovídala aktuálnímu časovému pásmu v Německu, zadejte na příkazovém řádku následující:

> **Nastavte TZ = GST 1GDT**

Tento příkaz používá GST k označení německého standardního času, předpokládá, že čas UTC je jednu hodinu za Německem (nebo jinými slovy, Německo je hodinu před časem UTC) a které předpokládá, že Německo dodržuje letní čas.

Pokud **TZ** hodnota není nastavená, **_tzset –** pokusí použít informace o časovém pásmu určeném operačního systému. V operačním systému Windows je tato informace zadána v aplikaci datum/čas v Ovládacích panelech. Pokud **_tzset –** nemůže získat tyto informace, použije PST8PDT ve výchozím nastavení, což znamená tichomořské časové pásmo.

Na základě **TZ** hodnotu proměnné prostředí, jsou následující hodnoty přiřazeny globálním proměnným **_daylight**, **_timezone**, a **_tzname** při **_tzset –** se volá:

|Globální proměnná|Popis|Výchozí hodnota|
|---------------------|-----------------|-------------------|
|**_daylight**|Nenulová hodnota, pokud je zóna letního času podle **TZ** nastavení; jinak 0.|1|
|**_timezone**|Rozdíl v sekundách mezi místním časem a UTC.|28800 (28800 sekund se rovná 8 hodin)|
|**_tzname**[0]|Řetězcová hodnota názvu časového pásma z **TZ** proměnné prostředí; prázdná, pokud **TZ** nebyla nastavena.|PST|
|**_tzname**[1]|Hodnota řetězce pásma letního času; prázdný, pokud je zóna letního času vynecháno z **TZ** proměnné prostředí.|PDT|

Výchozí hodnoty uvedené v předchozí tabulce pro **_daylight** a **_tzname** pole odpovídají "PST8PDT". Pokud je zóna letního času vynecháno z **TZ** proměnné prostředí, hodnota **_daylight** je 0 a [_ftime](ftime-ftime32-ftime64.md), [gmtime](gmtime-gmtime32-gmtime64.md)a [localtime](localtime-localtime32-localtime64.md) funkce vrátí 0 pro jejich příznaky letního času.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_tzset**|\<Time.h >|

**_Tzset –** funkce je specifické pro společnost Microsoft. Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
