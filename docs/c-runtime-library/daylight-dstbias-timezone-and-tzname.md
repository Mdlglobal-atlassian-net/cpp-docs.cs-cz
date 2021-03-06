---
title: _daylight, _dstbias, _timezone a _tzname
ms.date: 11/04/2016
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
ms.openlocfilehash: 3f9f78d0798140399960cade7ead408f958450ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344633"
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight, _dstbias, _timezone a _tzname

`_daylight`, `_dstbias`, `_timezone`, a `_tzname` se používají v některých rutin datum a čas provést úpravy místního času. Tyto globální proměnné jsou zastaralé pro bezpečnější funkční verze, které by měl být zastoupen globální proměnné.

|Globální proměnná|Ekvivalentní|
|---------------------|---------------------------|
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|

Jsou deklarované v Time.h následujícím způsobem.

## <a name="syntax"></a>Syntaxe

```
extern int _daylight;
extern int _dstbias;
extern long _timezone;
extern char *_tzname[2];
```

## <a name="remarks"></a>Poznámky

Volání `_ftime`, `localtime`, nebo `_tzset`, hodnoty `_daylight`, `_dstbias`, `_timezone`, a `_tzname` se stanoví z hodnoty `TZ` proměnné prostředí. Pokud explicitně nenastavíte hodnotu `TZ`, `_tzname[0]` a `_tzname[1]` obsahovat výchozí nastavení "PST" a "PDT" v uvedeném pořadí.  Čas zpracování funkce ([_tzset –](../c-runtime-library/reference/tzset.md), [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md), a [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) pokus o nastavení hodnoty `_daylight`, `_dstbias` a `_timezone` podle dotaz na operační systém pro výchozí hodnotu každé proměnné. Časové pásmo hodnoty globální proměnné jsou uvedeny v následující tabulce.

|Proměnná|Value|
|--------------|-----------|
|`_daylight`|Nenulové, pokud je zóna letního času (DST) je určena v `TZ` nebo určené v operačním systému, jinak 0. Výchozí hodnota je 1.|
|`_dstbias`|Posun na letní čas.|
|`_timezone`|Rozdíl v sekundách mezi UTC a místním časem. Výchozí hodnota je 28 800.|
|`_tzname[0]`|Název časového pásma odvozen od `TZ` proměnné prostředí. Výchozí hodnota je "PST".|
|`_tzname[1]`|Název zóny letního času odvozen od `TZ` proměnné prostředí. Výchozí hodnota je "PDT" (tichomořského letního času).|

## <a name="see-also"></a>Viz také:

[Globální proměnné](../c-runtime-library/global-variables.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
