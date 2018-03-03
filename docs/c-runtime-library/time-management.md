---
title: "Čas správy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4cf86c854345244eafff80392cdc575d026c61ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="time-management"></a>Správa času
Pomocí těchto funkcí získat aktuální čas a převést, upravit a uložit jej podle potřeby. Aktuální čas je čas systému.  
  
 `_ftime` a `localtime` použít rutiny `TZ` proměnné prostředí. Pokud `TZ` není nastaven, běhové knihovny se pokusí použít časové pásmo informace uvedené v operačním systému. Pokud tyto informace jsou k dispozici, použijte tyto funkce na výchozí hodnotu PST8PDT. Další informace o `TZ`, najdete v části [_tzset –](../c-runtime-library/reference/tzset.md); také zobrazit [_daylight, časové pásmo a _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).  
  
### <a name="time-routines"></a>Čas rutiny  
  
|Funkce|Použití|  
|--------------|---------|  
|[asctime –, _wasctime –](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s –, _wasctime_s –](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Převod z typu čas `struct tm` na řetězec znaků. Verze tyto funkce s `_s` příponu jsou bezpečnější.|  
|[clock](../c-runtime-library/reference/clock.md)|Vrátí Doba uplynulá wall – hodiny pro proces.|  
|[CTime –, _ctime32 –, _ctime64 –, _wctime –, _wctime32 –, _wctime64 –](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [_ctime_s, _ctime32_s –, _ctime64_s –, _wctime_s –, _wctime32_s –, _wctime64_s –](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Převod z typu čas `time_t`, `__time32_t` nebo `__time64_t` na řetězec znaků. Verze tyto funkce s `_s` příponu jsou bezpečnější.|  
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Výpočetní rozdíl mezi dvěma časy.|[System::DateTime:: odečtena](https://msdn.microsoft.com/en-us/library/system.datetime.subtract.aspx)|  
|[_ftime –, _ftime32 –, _ftime64 –](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s – _ftime32_s –, _ftime64_s –](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Uložení aktuální systémový čas v proměnné typu `struct _timeb` nebo typ `struct __timeb64` verzích tyto funkce s `_s` příponu jsou bezpečnější.|  
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Nastavte čas změny na otevření souboru|  
|[gmtime –, _gmtime32 –, _gmtime64 –](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s – _gmtime32_s –, _gmtime64_s –](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Převod z typu čas `time_t` k `struct tm` nebo z typu `__time64_t` k `struct tm`. Verze tyto funkce s `_s` příponu jsou bezpečnější.|  
|[místní čas, _localtime32 –, _localtime64 –](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s – _localtime32_s –, _localtime64_s –](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Převod z typu čas `time_t` k `struct tm` nebo z typu `__time64_t` k `struct tm` s místní oprava. Verze tyto funkce s `_s` příponu jsou bezpečnější.|  
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Převeďte čas na hodnotu kalendáře v greenwichský střední čas.|  
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Převeďte čas na hodnotu kalendáře.|  
|[_strdate –, _wstrdate –](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s –, _wstrdate_s –](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Vrátí aktuální systémový datum jako řetězec. Verze tyto funkce s `_s` příponu jsou bezpečnější.|  
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Řetězec formátu data a času pro mezinárodní použití.|  
|[_strtime –, _wstrtime –](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s –, _wstrtime_s –](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Vrátí aktuální systémový čas jako řetězec. Verze tyto funkce s `_s` příponu jsou bezpečnější.|  
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|Získat aktuální systémový čas jako typ `time_t`, `__time32_t` nebo jako typ `__time64_t`.|  
|[_tzset](../c-runtime-library/reference/tzset.md)|Nastavení proměnných externí čas od času proměnnou prostředí `TZ`.|  
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Nastavte čas změny pro zadaný soubor pomocí aktuálního času nebo času hodnotou uloženou ve struktuře.|  
  
> [!NOTE]
>  Ve všech verzích Microsoft C/C++ s výjimkou Microsoft C/C++ version 7.0 a ve všech verzích Visual C++ vrátí funkce čas jako počet sekund uběhlých od půlnoci na 1. ledna 1970 aktuální čas. V Microsoft C/C++ version 7.0 `time` jako počet sekund uběhlých od půlnoci na 31. prosince 1899 vrátí aktuální čas.  
  
> [!NOTE]
>  Ve verzích Visual C++ a Microsoft C/C++ před Visual C++ 2005 `time_t` byl `long int` (32bitová verze) a nelze jej proto použít pro data po 3:14:07 19. ledna 2038, UTC. `time_t`Nyní je ekvivalentní `__time64_t` ve výchozím nastavení, ale definování `_USE_32BIT_TIME_T` změny `time_t` k `__time32_t` a vynutí mnoho časové funkce k volání verze, které trvat 32bitovou verzi `time_t`. Další informace najdete v tématu [standardní typy](../c-runtime-library/standard-types.md) a komentáře v dokumentaci pro jednotlivé časové funkce.  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)