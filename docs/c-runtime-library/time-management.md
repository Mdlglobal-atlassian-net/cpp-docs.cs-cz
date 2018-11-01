---
title: Správa času
ms.date: 11/04/2016
f1_keywords:
- c.memory
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
ms.openlocfilehash: e7b34101e6c09238316d7dc0ebb223ede25d60bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623766"
---
# <a name="time-management"></a>Správa času

Tyto funkce můžete použijte k získání aktuální čas a převést, upravte a uložte ho podle potřeby. Aktuální čas je systémový čas.

**_Ftime** a **localtime** použít rutiny **TZ** proměnné prostředí. Pokud **TZ** není nastaven, pokusí se použít informace o časovém pásmu, který je určený operační systém knihovny run-time. Pokud tyto informace jsou k dispozici, tyto funkce použijte výchozí hodnotu PST8PDT. Další informace o **TZ**, naleznete v tématu [_tzset –](../c-runtime-library/reference/tzset.md); zobrazit také [_daylight, časové pásmo a _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

### <a name="time-routines"></a>Time Routines

|Funkce|Použití|
|--------------|---------|
|[asctime, _wasctime – –](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s – –](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Převod z typu času **struktura tm** na řetězec znaků. Verze těchto funkcí s **_Malá** přípona jsou bezpečnější.|
|[clock](../c-runtime-library/reference/clock.md)|Vrátí skutečný uplynulý čas pro proces.|
|[CTime – _ctime32 –, _ctime64, _wctime, _wctime32 –, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [_ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Převod z typu času **time_t**, **__time32_t** nebo **__time64_t –** na řetězec znaků. Verze těchto funkcí s **_Malá** přípona jsou bezpečnější.|
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Vypočítat rozdíl mezi dvěma časy.|[System::DateTime:: odečíst](https://msdn.microsoft.com/library/system.datetime.subtract.aspx)|
|[_ftime _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Store aktuální systémový čas v proměnné typu **_timeb – struktura** nebo typ **__timeb64 – struktura** verze těchto funkcí s **_Malá** přípona jsou bezpečnější.|
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Nastavte čas změny na otevřený soubor|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s – _gmtime32_s –, _gmtime64_s –](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Čas převést z typu **time_t** k **tm – struktura** nebo z typu **__time64_t –** k **struktura tm**. Verze těchto funkcí s **_Malá** přípona jsou bezpečnější.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s – _localtime32_s –, _localtime64_s –](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Čas převést z typu **time_t** k **tm – struktura** nebo z typu **__time64_t –** k **struktury tm** s místní opravy. Verze těchto funkcí s **_Malá** přípona jsou bezpečnější.|
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Převod času na hodnotu kalendáře v greenwichský střední čas.|
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Převod času na hodnotu kalendáře.|
|[_strdate – _wstrdate –](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s – _wstrdate_s –](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Vrátí aktuální systémový datum jako datový typ string. Verze těchto funkcí s **_Malá** přípona jsou bezpečnější.|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Řetězec formátu data a času pro mezinárodní použití.|
|[_strtime – _wstrtime –](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s – _wstrtime_s –](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Vrátí aktuální systémový čas jako datový typ string. Verze těchto funkcí s **_Malá** přípona jsou bezpečnější.|
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|Získat aktuální systémový čas jako typ **time_t**, **__time32_t** nebo jako typ **__time64_t –**.|
|[_tzset](../c-runtime-library/reference/tzset.md)|Nastavení proměnných externí čas z proměnné prostředí času **TZ**.|
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Nastavte čas změny pro zadaný soubor pomocí aktuálního času nebo času hodnota uložená ve struktuře.|

> [!NOTE]
> Ve všech verzích Microsoft C/C++ s výjimkou Microsoft C/C++ version 7.0 a ve všech verzích aplikace Visual C++ funkce čas vrátí aktuální čas jako dobu v sekundách uplynulých od půlnoci na 1. ledna 1970. V Microsoft C/C++ version 7.0 **čas** jako dobu v sekundách uplynulých od půlnoci na 31. prosince 1899 vrátí aktuální čas.

> [!NOTE]
> Ve verzích Visual C++ a Microsoft C/C++ před Visual C++ 2005 **time_t** byla **dlouhé** **int** (32bitová verze) a proto jej nelze použít pro data za 3:14:07 19. ledna 2038 , UTC. **time_t** je ekvivalentní **__time64_t –** ve výchozím nastavení, ale definování **_USE_32BIT_TIME_T** změny **time_t** k **__time32_t** a vynutí mnoho času funkce pro volání verze, které trvat 32-bit **time_t**. Další informace najdete v tématu [standardní typy](../c-runtime-library/standard-types.md) a komentářů v dokumentaci pro jednotlivé časové funkce.

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
