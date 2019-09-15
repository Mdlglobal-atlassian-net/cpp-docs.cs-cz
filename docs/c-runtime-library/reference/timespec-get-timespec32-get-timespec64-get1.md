---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 11/04/2016
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: c0517c974bf58d502133ccd9868149bd178790d6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957622"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get, _timespec32_get, _timespec64_get

Nastaví interval, na který odkazuje první argument na aktuální časový čas v kalendáři na základě zadané časové základny.

## <a name="syntax"></a>Syntaxe

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>Parametry

*time_spec*<br/>
Ukazatel na strukturu, která je nastavená na čas v sekundách a nanosekundách od začátku epochau.

*base*<br/>
Nenulová hodnota specifická pro specifickou implementaci, která určuje časovou základnu.

## <a name="return-value"></a>Návratová hodnota

Hodnota *Base* v případě úspěchu, jinak vrátí hodnotu nula.

## <a name="remarks"></a>Poznámky

Funkce **timespec_get** nastaví aktuální čas ve struktuře, na kterou ukazuje argument *time_spec* . Všechny verze této struktury mají dva členy, **tv_sec** a **tv_nsec**. Hodnota **tv_sec** je nastavená na celý počet sekund a **tv_nsec** na celočíselný počet nanosekund, který se zaokrouhluje na rozlišení systémových hodin od začátku epocha určeného *základem*.

**Specifické pro společnost Microsoft**

Tyto funkce podporují pouze **TIME_UTC** jako *základní* hodnotu. Tím se hodnota *time_spec* nastaví na počet sekund a nanosekund od spuštění epocha, půlnoc, 1. ledna 1970, koordinovaný světový čas (UTC). V _timespec32 **struktury**je **tv_sec** hodnota **__time32_t** . V _timespec64 **struktury**je **tv_sec** hodnota **__time64_t** . V timespec **struktury**je **tv_sec** typ **time_t** , což je 32 bitů nebo 64 bitů v závislosti na tom, zda je definován makro preprocesoru _USE_32BIT_TIME_T. Funkce **timespec_get** je vložená funkce, která volá **_timespec32_get** , pokud je definována _USE_32BIT_TIME_T; v opačném případě volá **_timespec64_get**.

**Specifické pro konec Microsoftu**

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**timespec_get**, **_timespec32_get**, **_timespec64_get**|C: \<Time. h >, C++: \<CTime – > nebo \<Time. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
