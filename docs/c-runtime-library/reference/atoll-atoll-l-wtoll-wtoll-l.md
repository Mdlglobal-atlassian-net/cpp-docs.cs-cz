---
title: atoll, _atoll_l, _wtoll, _wtoll_l
ms.date: 11/04/2016
api_name:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tstoll_l
- _wtoll
- _atoll_l
- _ttoll
- _tstoll
- _wtoll_l
- atoll
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
ms.openlocfilehash: f1b5fca9c3428bce26a8a40cf8271760fa97b10b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939477"
---
# <a name="atoll-_atoll_l-_wtoll-_wtoll_l"></a>atoll, _atoll_l, _wtoll, _wtoll_l

Převede řetězec na **dlouhé** **dlouhé** celé číslo.

## <a name="syntax"></a>Syntaxe

```C
long long atoll(
   const char *str
);
long long _wtoll(
   const wchar_t *str
);
long long _atoll_l(
   const char *str,
   _locale_t locale
);
long long _wtoll_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec, který má být převeden.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí **dlouhou** **dlouhou** hodnotu, která je vytvořena interpretací vstupních znaků jako čísla. Návratová hodnota pro **atol** je 0, pokud vstup nelze převést na hodnotu daného typu.

Pro přetečení s velkými celočíselnými hodnotami, **Palmyra** vrátí **LLONG_MAX**a pro přetečení s velkými zápornými hodnotami vrátí **LLONG_MIN**.

V všech případech mimo rozsah je **errno** nastaveno na **ERANGE**. Pokud předaný parametr má **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Tyto funkce převádějí řetězec znaků na **dlouhé** **dlouhé** celočíselné hodnoty.

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako číselnou hodnotu zadaného typu. Funkce zastaví čtení vstupního řetězce u prvního znaku, který nemůže rozpoznat jako součást čísla. Tento znak může být znak null (' \ 0 ' nebo L ' \ 0 '), který ukončí řetězec.

Argument *str* pro **atol** má následující formu:

> [*prázdné znaky*] [*Sign*] [*číslice*]

*Mezera* se skládá z mezer nebo znaků tabulátoru, které jsou ignorovány; *znaménko* je buď znaménko plus (+) nebo minus (-); a *číslice* jsou jednou nebo více číslicemi.

**_wtoll** je identický s **atol** s tím rozdílem, že jako parametr přijímá řetězec s velkým počtem znaků.

Verze těchto funkcí, které mají příponu **_l** , jsou shodné s verzemi, které ji nemají, s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoll**|**Palmyra**|**Palmyra**|**_wtoll**|
|**_tstoll_l**|**_atoll_l**|**_atoll_l**|**_wtoll_l**|
|**_ttoll**|**_atoll**|**_atoll**|**_wtoll**|

## <a name="requirements"></a>Požadavky

|Rutiny|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**atoll**, **_atoll_l**|\<stdlib.h>|
|**_wtoll**, **_wtoll_l**|\<Stdlib. h > nebo \<WCHAR. h >|

## <a name="example"></a>Příklad

Tento program ukazuje, jak používat funkce **Palmyra** pro převod čísel uložených jako řetězce na číselné hodnoty.

```C
// crt_atoll.c
// Build with: cl /W4 /Tc crt_atoll.c
// This program shows how to use the atoll
// functions to convert numbers stored as
// strings to numeric values.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main(void)
{
    char *str = NULL;
    long long value = 0;

    // An example of the atoll function
    // with leading and trailing white spaces.
    str = "  -27182818284 ";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoll("  -27182818284 ") = -27182818284
Function: atoll("314127.64") = 314127
Function: atoll("3336402735171707160320") = 9223372036854775807
Overflow condition occurred.
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
