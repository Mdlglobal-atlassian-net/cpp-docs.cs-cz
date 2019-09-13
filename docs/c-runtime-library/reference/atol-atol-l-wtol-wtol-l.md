---
title: atol, _atol_l, _wtol, _wtol_l
ms.date: 11/04/2016
api_name:
- atol
- _wtol_l
- _wtol
- _atol_l
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
- _atol_l
- _ttol_l
- _tstol_l
- _tstol
- _wtol
- _ttol
- _wtol_l
helpviewer_keywords:
- tstol function
- atol function
- ttol function
- _atol_l function
- _tstol_l function
- string conversion, to integers
- _tstol function
- _ttol function
- _ttol_l function
- atol_l function
- wtol_l function
- _wtol_l function
- wtol function
- _wtol function
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
ms.openlocfilehash: 04a2951a48e6dd2c3820551e0fc603ad4ed81086
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943584"
---
# <a name="atol-_atol_l-_wtol-_wtol_l"></a>atol, _atol_l, _wtol, _wtol_l

Převede řetězec na dlouhé celé číslo.

## <a name="syntax"></a>Syntaxe

```C
long atol(
   const char *str
);
long _atol_l(
   const char *str,
   _locale_t locale
);
long _wtol(
   const wchar_t *str
);
long _wtol_l(
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

Každá funkce vrací **dlouhou** hodnotu vytvořenou interpretací vstupních znaků jako čísla. Návratová hodnota je 0L pro **atol** , pokud vstup nelze převést na hodnotu tohoto typu.

V případě přetečení s velkými objemy integrálních hodnot vrátí **atol** hodnotu **LONG_MAX**; v případě přetečení s velkými zápornými celočíselnými hodnotami se vrátí **LONG_MIN** . V všech případech mimo rozsah je **errno** nastaveno na **ERANGE**. Pokud předaný parametr má **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Tyto funkce převádějí řetězec znaků na hodnotu typu Long Integer (**atol**).

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako číselnou hodnotu zadaného typu. Funkce zastaví čtení vstupního řetězce u prvního znaku, který nemůže rozpoznat jako součást čísla. Tento znak může být znak null (' \ 0 ' nebo L ' \ 0 ') ukončující řetězec.

Argument *str* pro **atol** má následující tvar:

> [*prázdné znaky*] [*Sign*] [*číslice*]]

*Mezera* se skládá z mezer nebo znaků tabulátoru, které jsou ignorovány; *znaménko* je buď znaménko plus (+) nebo minus (-); a *číslice* jsou jednou nebo více číslicemi.

**_wtol** je shodná s **atol** s tím rozdílem, že používá řetězec s velkým počtem znaků.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstol**|**atol**|**atol**|**_wtol**|
|**_ttol**|**atol**|**atol**|**_wtol**|

## <a name="requirements"></a>Požadavky

|Rutiny|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**atol**|\<stdlib.h>|
|**_atol_l**, **_wtol**, **_wtol_l**|\<Stdlib. h > a \<WCHAR. h >|

## <a name="example"></a>Příklad

Tento program ukazuje, jak mohou být čísla uložená jako řetězce převedeny na číselné hodnoty pomocí funkce **atol** .

```C
// crt_atol.c
// This program shows how numbers stored as
// strings can be converted to numeric values
// using the atol functions.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    long    value = 0;

    // An example of the atol function
    // with leading and trailing white spaces.
    str = "  -2309 ";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );

    // Another example of the atol function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );

    // Another example of the atol function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atol( "  -2309 " ) = -2309
Function: atol( "314127.64" ) = 314127
Function: atol( "3336402735171707160320" ) = 2147483647
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
