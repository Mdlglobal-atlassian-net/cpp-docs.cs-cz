---
title: _strtime_s, _wstrtime_s
ms.date: 11/04/2016
apiname:
- _wstrtime_s
- _strtime_s
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
ms.openlocfilehash: 579c4a99b52c66bd14cea947eaa1f301cc1127e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642361"
---
# <a name="strtimes-wstrtimes"></a>_strtime_s, _wstrtime_s

Zkopírujte aktuální čas do vyrovnávací paměti. Jde o verzích [_strtime – _wstrtime –](strtime-wstrtime.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť, alespoň 10 bajtů, kam se budou zapisovat čas.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu.

Pokud dojde k chybě, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Vrácená hodnota je kód chyby, pokud dojde k selhání. Kódy chyb jsou definovány v ERRNO. H. v následující tabulce pro přesné chyb generovaných touto funkcí. Další informace o chybových kódech naleznete v tématu [errno – konstanty](../../c-runtime-library/errno-constants.md).

### <a name="error-conditions"></a>Chybové podmínky

|*Vyrovnávací paměti*|*numberOfElements*|Vrátí|Obsah *vyrovnávací paměti*|
|--------------|------------------------|------------|--------------------------|
|**HODNOTU NULL**|(žádné)|**EINVAL**|Nezměněno|
|Není **NULL** (odkazuje na platnou vyrovnávací paměť)|0|**EINVAL**|Nezměněno|
|Není **NULL** (odkazuje na platnou vyrovnávací paměť)|0 < velikost < 9|**EINVAL**|Prázdný řetězec|
|Není **NULL** (odkazuje na platnou vyrovnávací paměť)|Velikost > 9|0|Aktuální čas ve formátu zadané v poli poznámky|

## <a name="security-issues"></a>Problémy se zabezpečením

Předání neplatný jinou hodnotu než**NULL** hodnota vyrovnávací paměti se vést k narušení přístupu-li *numberOfElements* parametr je větší než 9.

Předáním hodnoty *numberOfElements* , který je větší než skutečná velikost vyrovnávací paměti způsobí přetečení vyrovnávací paměti.

## <a name="remarks"></a>Poznámky

Poskytují bezpečnější verze těchto funkcí [_strtime –](strtime-wstrtime.md) a [_wstrtime –](strtime-wstrtime.md). **_Strtime_s –** funkce kopíruje do vyrovnávací paměti, na které odkazuje aktuálním místním časem *timestr*. Čas je formátován jako **hh: mm:** kde **hh** dvou číslic představující hodiny ve 24hodinovém formátu, je **mm** je dvou číslic představující minut za hodinu a **ss** je dvou číslic představující sekund. Například řetězec **18:23:44** představuje 23 minut a 44 sekund po 6 hodin Vyrovnávací paměť musí být alespoň 9 bajty; Skutečná velikost je určená druhý parametr.

**_wstrtime –** je verze širokého znaku **_strtime –**; argument a návratová hodnota funkce **_wstrtime –** jsou širokoznaké řetězce. Tyto funkce chovají identicky jinak.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky (tím eliminuje nutnost zadat argument velikosti) a dokážou automaticky nahradit starší, nezabezpečené funkce jejími novějšími, zabezpečené protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Mapování obecného textu rutiny:

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strtime_s**|\<Time.h >|
|**_wstrtime_s**|\<Time.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
