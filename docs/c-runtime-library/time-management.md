---
title: Časová správa
ms.date: 11/04/2016
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
ms.openlocfilehash: 24859a0b35274881b03b960807904ed38b19e354
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444586"
---
# <a name="time-management"></a>Časová správa

Pomocí těchto funkcí získáte aktuální čas a v případě potřeby ho můžete převést, upravit a uložit. Aktuální čas je systémový čas.

Rutiny **_ftime** a **localtime** používají proměnnou prostředí **TZ** . Pokud není zadán parametr **TZ** , knihovna za běhu se pokusí použít informace o časovém pásmu určené operačním systémem. Pokud tyto informace nejsou k dispozici, používají tyto funkce výchozí hodnotu PST8PDT. Další informace o **TZ**najdete v tématu [_tzset](../c-runtime-library/reference/tzset.md); Viz také [_daylight, časové pásmo a _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

### <a name="time-routines"></a>Časové rutiny

|Funkce|Použití|
|--------------|---------|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md) [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Převede čas z typu **Struktura TM** na řetězec znaků. Verze těchto funkcí s příponou **_s** jsou bezpečnější.|
|[clock](../c-runtime-library/reference/clock.md)|Vrátí uplynulý čas na zeď pro proces.|
|[CTime –, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), _ctime_s [, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Převede čas z typu **time_t**, **__time32_t** nebo **__time64_t** na řetězec znaků. Verze těchto funkcí s příponou **_s** jsou bezpečnější.|
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Rozdíl mezi výpočty mezi dvěma časy.|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s, _ftime32_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) _ftime64_s|Uloží aktuální systémový čas do proměnné typu **struktura _timeb** nebo struktura typu **__timeb64** verze těchto funkcí s příponou **_s** jsou bezpečnější.|
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Nastavit čas změny pro otevřený soubor|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Převeďte čas z typu **time_t** na **struct tm** nebo z typu **__time64_t** na **struct tm**. Verze těchto funkcí s příponou **_s** jsou bezpečnější.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Převeďte čas z typu **time_t** na **struct tm** nebo z typu **__time64_t** na **struct tm** s místní opravou. Verze těchto funkcí s příponou **_s** jsou bezpečnější.|
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Převede čas na hodnotu kalendáře v Greenwichovém středním čase.|
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Převede čas na hodnotu kalendáře.|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Vrátí aktuální systémové datum jako řetězec. Verze těchto funkcí s příponou **_s** jsou bezpečnější.|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Formát řetězce data a času pro mezinárodní použití|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s _wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Vrátí aktuální systémový čas jako řetězec. Verze těchto funkcí s příponou **_s** jsou bezpečnější.|
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|Získá aktuální systémový čas jako typ **time_t**, **__time32_t** nebo jako typ **__time64_t**.|
|[_tzset](../c-runtime-library/reference/tzset.md)|Nastavte externí časové proměnné z proměnné čas prostředí – **TZ**.|
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Nastavte čas změny pro zadaný soubor pomocí hodnoty aktuální čas nebo čas uložený ve struktuře.|

> [!NOTE]
> Ve všech verzích Microsoft C/C++ s výjimkou společnosti MicrosoftC++ c/verze 7,0 a ve všech verzích vizuálu C++vrátí funkce time aktuální čas, protože počet sekund uplynulý od půlnoci od 1. ledna 1970. V jazyce Microsoft CC++ /verze 7,0 **čas** vrácený aktuálním časem jako počet sekund uplynulý od půlnoci 31. prosince 1899.

> [!NOTE]
> Ve verzích vizuálů Visual C++ a Microsoft C/C++ před visual Studio 2005 byl **time_t** **dlouhé** **celé číslo** (32 bitů), a proto se nedá použít pro datum poslední 3:14:07 19. ledna, 2038, UTC. **time_t** je teď ve výchozím nastavení ekvivalentní **__time64_t** , ale definuje **_USE_32BIT_TIME_T** změny **time_t** **__time32_t** a vynutí mnoho funkcí, které budou volat verze, které přebírají 32 **time_t**. Další informace najdete v tématu [standardní typy](../c-runtime-library/standard-types.md) a komentáře v dokumentaci pro jednotlivé časové funkce.

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
