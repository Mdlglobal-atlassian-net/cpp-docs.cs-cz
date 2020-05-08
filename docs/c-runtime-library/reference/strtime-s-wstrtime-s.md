---
title: _strtime_s, _wstrtime_s
ms.date: 4/2/2020
api_name:
- _wstrtime_s
- _strtime_s
- _o__strtime_s
- _o__wstrtime_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
ms.openlocfilehash: 54828bf894ffc9062125c9680ec087cdf929b1a2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910929"
---
# <a name="_strtime_s-_wstrtime_s"></a>_strtime_s, _wstrtime_s

Zkopírujte aktuální čas do vyrovnávací paměti. Jedná se o verze [_strtime, _wstrtime](strtime-wstrtime.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _strtime_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrtime_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strtime_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrtime_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Vyrovnávací paměť, nejméně 10 bajtů, kde bude zapsán čas.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu.

Pokud dojde k chybě, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Návratová hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v ERRNO. Y v následující tabulce najdete přesné chyby generované touto funkcí. Další informace o kódech chyb naleznete v tématu [konstanty errno](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Chybové stavy

|*vyrovnávací paměti*|*numberOfElements*|Vrátit|Obsah *vyrovnávací paměti*|
|--------------|------------------------|------------|--------------------------|
|**PLATNOST**|jakýmikoli|**EINVAL**|Neupraveno|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|0|**EINVAL**|Neupraveno|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|0 < velikosti < 9|**EINVAL**|Prázdný řetězec|
|NOT **null** (ukazující na platnou vyrovnávací paměť)|Velikost > 9|0|Aktuální čas formátovaný podle zadání v komentářích|

## <a name="security-issues"></a>Problémy se zabezpečením

Předání neplatné hodnoty, která není**null** pro vyrovnávací paměť, bude mít za následek porušení přístupu, pokud je parametr *numberOfElements* větší než 9.

Předání hodnoty pro *numberOfElements* , která je větší než skutečná velikost vyrovnávací paměti, způsobí přetečení vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

Tyto funkce poskytují bezpečnější verze [_strtime](strtime-wstrtime.md) a [_wstrtime](strtime-wstrtime.md). Funkce **_strtime_s** kopíruje aktuální místní čas do vyrovnávací paměti, na kterou odkazuje *timestr*. Čas je formátován jako **HH: mm: SS** , kde **HH** je dvě číslice představující hodinu ve 24hodinovém zápisu, **mm** jsou dvě číslice představující minuty po hodinách a **SS** jsou dvě číslice představující sekundy. Například řetězec **18:23:44** představuje 23 minut a 44 sekund za 6 hodin. Vyrovnávací paměť musí být aspoň 9 bajtů dlouhá. Skutečná velikost je určena druhým parametrem.

**_wstrtime** je verze **_strtime**s velkým znakem; argument a návratová hodnota **_wstrtime** jsou řetězce s velkým počtem znaků. Tyto funkce se chovají identicky jinak.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Verze knihovny ladění těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFE. K zakázání tohoto chování použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapování rutiny obecného textu:

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strtime_s**|\<Time. h>|
|**_wstrtime_s**|\<Time. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// strtime_s.c

#include <time.h>
#include <stdio.h>

int main()
{
    char tmpbuf[9];
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    err = _strtime_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
      exit(1);
    }
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    err = _strdate_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
       exit(1);
    }
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

}
```

```Output
OS time:            14:37:49
OS date:            04/25/03
```

## <a name="see-also"></a>Viz také

[Časová správa](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
