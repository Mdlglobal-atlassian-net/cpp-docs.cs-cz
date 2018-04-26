---
title: _atoi64 –, _atoi64_l –, _wtoi64 –, _wtoi64_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _atoi64_l
- _wtoi64
- _atoi64
- _wtoi64_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _atoi64
- _tstoi64
- _ttoi64
- wtoi64
- _tstoi64_l
- atoi64
- _wtoi64_l
- _wtoi64
- wtoi64_l
- _atoi64_l
- atoi64_l
dev_langs:
- C++
helpviewer_keywords:
- tstoi64 function
- wtoi64 function
- atoi64_l function
- _ttoi64 function
- string conversion, to integers
- wtoi64_l function
- atoi64 function
- _tstoi64 function
- _atoi64_l function
- _wtoi64_l function
- ttoi64 function
- _wtoi64 function
- _atoi64 function
ms.assetid: 2c3e30fd-545d-4222-8364-0c5905df9526
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69afae8702d707395b09c4848d62aebf6b24aa8f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="atoi64-atoi64l-wtoi64-wtoi64l"></a>_atoi64, _atoi64_l, _wtoi64, _wtoi64_l

Převede řetězec na 64bitové celé číslo.

## <a name="syntax"></a>Syntaxe

```C
__int64 _atoi64(
   const char *str
);
__int64 _wtoi64(
   const wchar_t *str
);
__int64 _atoi64_l(
   const char *str,
   _locale_t locale
);
__int64 _wtoi64_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str –*<br/>
Řetězec, který má být převeden.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrátí **__int64** hodnota vyprodukované interpretace vstupu znaky jako číslo. Vrácená hodnota je 0 pro **_atoi64 –** Pokud vstup nelze převést na hodnotu daného typu.

V případě přetečení s velké kladné celočíselné hodnoty **_atoi64 –** vrátí **I64_MAX** a **I64_MIN** v případě přetečení s velké záporné celočíselné hodnoty.

Ve všech případech out-of-range **errno** je nastaven na **erange –**. Pokud parametr byl předán v **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátí 0.

## <a name="remarks"></a>Poznámky

Tyto funkce převést znakového řetězce na hodnotu 64bitové celé číslo.

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako hodnotu zadaného typu. Funkce zastaví čtení vstupní řetězec u prvního znaku, který nelze rozpoznat jako součást číslo. Tento znak může být znak hodnoty null ('\0' nebo L '\0') ukončující řetězec.

*Str* argument **_atoi64 –** má následující formát:

> [*prázdné*] [*přihlašovací*] [*číslic*]

A *prázdné* se skládá z místa nebo kartě znaků, které se mají ignorovat; *přihlašovací* je buď plus (+) nebo minus (-) a *číslic* jsou jeden nebo více číslic.

**_wtoi64 –** je stejný jako **_atoi64 –** s tím rozdílem, že trvá řetězec široké znaků jako parametr.

Verze tyto funkce s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí předaná místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoi64 –**|**_atoi64**|**_atoi64**|**_wtoi64**|
|**_ttoi64 –**|**_atoi64**|**_atoi64**|**_wtoi64**|

## <a name="requirements"></a>Požadavky

|Rutiny|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_atoi64 –**, **_atoi64_l –**|\<stdlib.h>|
|**_wtoi64 –**, **_wtoi64_l –**|\<stdlib.h > nebo \<wchar.h >|

## <a name="example"></a>Příklad

Tento program ukazuje, jak lze převést čísla uložená jako řetězce do číselných hodnot pomocí **_atoi64 –** funkce.

```C
// crt_atoi64.c
// This program shows how numbers stored as
// strings can be converted to numeric values
// using the _atoi64 functions.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    __int64 value = 0;

    // An example of the _atoi64 function
    // with leading and trailing white spaces.
    str = "  -2309 ";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );

    // Another example of the _atoi64 function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );

    // Another example of the _atoi64 function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: _atoi64( "  -2309 " ) = -2309
Function: _atoi64( "314127.64" ) = 314127
Function: _atoi64( "3336402735171707160320" ) = -1
Overflow condition occurred.
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
