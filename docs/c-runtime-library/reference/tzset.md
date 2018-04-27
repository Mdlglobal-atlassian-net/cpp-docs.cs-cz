---
title: _tzset – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0df3f64f81520ed27c0bb79f683e28c1053d48f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="tzset"></a>_tzset

Sady času proměnné prostředí.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
void _tzset( void );
```

## <a name="remarks"></a>Poznámky

**_Tzset –** funkce používá aktuální nastavení proměnné prostředí **TZ** přiřadit hodnoty tři globální proměnné: **_daylight**, **_timezone** , a **_tzname**. Tyto proměnné jsou používány [_ftime –](ftime-ftime32-ftime64.md) a [místní čas](localtime-localtime32-localtime64.md) funkce k provedení oprav z koordinovaný světový čas (UTC), k místní čas a [čas](time-time32-time64.md) funkci, aby se výpočetní čas UTC z systémového času. Použijte následující syntaxi nastavit **TZ** proměnnou prostředí:

> **nastavit TZ =**_tzn_ \[ **+** &#124; **-**]*hh* \[ **:**_mm_\[**:**_ss_]] [*dzn*]

|Parametr|Popis|
|-|-|
*tzn*|Název časového pásma tří písmen, jako je například PST. Je nutné zadat správné posun z místního času na čas UTC.
*hh*|Rozdíl v hodinách mezi místním ČASEM a. Znaménko (+) volitelné pro kladné hodnoty.
*mm*|Počet minut. Oddělená od *hh* dvojtečkou (**:**).
*ss*|Sekund. Oddělená od *mm* dvojtečkou (**:**).
*dzn*|Například PDT tří písmen letní – ukládání časové pásmo. Pokud letní čas se nikdy platí v místě, nastavit **TZ** bez hodnoty pro *dzn*. Běhové knihovny jazyka C předpokládá Spojené státy pravidla pro implementaci výpočtu letní čas (letní čas).

> [!NOTE]
> Vezměte v potaz v oblasti výpočetních znaménko časový rozdíl. Protože časový rozdíl je posun z místního času na čas UTC (nikoli naopak), může být jeho přihlašovací opak může intuitivně očekávat. Časová pásma před časem UTC časový rozdíl je záporný; pro ty za čas UTC je kladné rozdíl.

Chcete-li například nastavit **TZ** proměnnou prostředí tak, aby odpovídaly aktuální časové pásmo v Německu, zadejte na příkazovém řádku následující:

> **nastavit TZ = GST 1GDT**

Tento příkaz GST používá k označení němčině (běžný čas), předpokládá, že UTC je jedna hodina za Německu (nebo jiná slova, která Německo je jedna hodina před časem UTC) a předpokládá, že Německo dodržuje – letní čas.

Pokud **TZ** hodnota není nastavena, **_tzset –** pokusí použít informace o časovém pásmu zadaný operační systém. V operačním systému Windows tyto informace je zadán v aplikaci datum a čas v Ovládacích panelech. Pokud **_tzset –** nelze získat tyto informace využívá PST8PDT ve výchozím nastavení, která označuje, že tichomořském časovém pásmu.

Na základě **TZ** hodnotu proměnné prostředí, následující hodnoty jsou přiřazeny k globální proměnné **_daylight**, **_timezone**, a **_tzname** při **_tzset –** se označuje jako:

|Globální proměnná|Popis|Výchozí hodnota|
|---------------------|-----------------|-------------------|
|**_daylight**|Nenulovou hodnotu, pokud letního času. ukládání časové pásmo je uveden v **TZ** nastavení; jinak hodnota 0.|1|
|**_timezone**|Rozdíl v sekundách mezi místní čas a čas UTC.|28800 (28 800 sekund rovná 8 hodin)|
|**_tzname**[0]|Hodnota názvu časového pásma z řetězec **TZ** proměnné prostředí; prázdný Pokud **TZ** nebyl nastaven.|PST|
|**_tzname**[1]|Řetězcová hodnota zóny letní--čas; prázdný, pokud je vynechaný letního času. ukládání časových pásem **TZ** proměnné prostředí.|PDT|

Výchozí hodnoty uvedené v předchozí tabulce pro **_daylight** a **_tzname** pole odpovídají "PST8PDT." Pokud je vynechaný zóny letního času **TZ** proměnné prostředí, hodnota **_daylight** je 0 a [_ftime –](ftime-ftime32-ftime64.md), [gmtime –](gmtime-gmtime32-gmtime64.md)a [místní čas](localtime-localtime32-localtime64.md) funkce vrátí 0 pro jejich příznaky letního času.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_tzset**|\<Time.h >|

**_Tzset –** je funkce specifická pro společnost Microsoft. Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
