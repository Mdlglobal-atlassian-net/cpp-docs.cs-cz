---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 4/2/2020
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
- _o__timespec32_get
- _o__timespec64_get
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
ms.openlocfilehash: fc6d91b076f2dd2e25c55d9cf7062e81c3fab11a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362488"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get, _timespec32_get, _timespec64_get

Nastaví interval, na který první argument ukazuje, na aktuální čas kalendáře na základě zadaného časového základu.

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
Ukazatel na strukturu, která je nastavena na čas v sekundách a nanosekundách od začátku epochy.

*base*<br/>
Nenulová hodnota specifická pro implementaci, která určuje časovou základnu.

## <a name="return-value"></a>Návratová hodnota

Hodnota *base,* pokud je úspěšná, jinak vrátí nulu.

## <a name="remarks"></a>Poznámky

Funkce **timespec_get** nastavují aktuální čas ve struktuře, na kterou je odkazováno *argumentem time_spec.* Všechny verze této struktury mají dva členy, **tv_sec** a **tv_nsec**. Hodnota **tv_sec** je nastavena na celý počet sekund a **tv_nsec** na integrální počet nanosekund, zaokrouhlený na rozlišení systémových hodin, od začátku epochy určené *bázou*.

**Specifické pro Microsoft**

Tyto funkce podporují pouze **TIME_UTC** jako *základní* hodnotu. Tím se nastaví *hodnota time_spec* na počet sekund a nanosekund od zahájení epochy, půlnoc, leden 1, 1970, koordinovaný světový čas (UTC). Ve **_timespec32 struktury** **_timespec32** **je tv_sec** **__time32_t** hodnota. Ve **_timespec64 struktury** **_timespec64**je **tv_sec** **__time64_t** hodnota. V **časové specifikace struktury** **je tv_sec** **typ time_t,** který je 32 bitů nebo 64 bitů v závislosti na **tom,** zda je definována makro preprocesorová makro _USE_32BIT_TIME_T. Funkce **timespec_get** je vsazená funkce, která volá **_timespec32_get,** pokud je definován_USE_32BIT_TIME_T jinak volá **_timespec64_get**.

**Ukončit microsoft specifické**

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**timespec_get** **_timespec32_get** **_timespec64_get**|C: \<time.h>, C++: \< \<ctime> nebo time.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
