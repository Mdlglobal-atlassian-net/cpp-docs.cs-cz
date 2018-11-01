---
title: atof, _atof_l, _wtof, _wtof_l
ms.date: 04/05/2018
apiname:
- _wtof_l
- atof
- _atof_l
- _wtof
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
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
ms.openlocfilehash: 6c2ec158ac0b75a861b5b226d33de113d76988cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471172"
---
# <a name="atof-atofl-wtof-wtofl"></a>atof, _atof_l, _wtof, _wtof_l

Převod řetězce na double.

## <a name="syntax"></a>Syntaxe

```C
double atof(
   const char *str
);
double _atof_l(
   const char *str,
   _locale_t locale
);
double _wtof(
   const wchar_t *str
);
double _wtof_l(
   const wchar_t *str,
   _locale_t locale
);
```

## <a name="parameters"></a>Parametry

*str*<br/>
Řetězec, který má být převeden.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí **double** hodnotu interpretací vstupních znaků jako číslo. Vrácená hodnota je 0,0, pokud vstup nelze převést na hodnotu daného typu.

Ve všech případech mimo rozsah **errno** je nastavena na **ERANGE**. Pokud parametr předaný **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátí 0.

## <a name="remarks"></a>Poznámky

Tyto funkce převádějí řetězec znaků na hodnotu s dvojitou přesností a plovoucí desetinnou čárkou.

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako hodnotu zadaného typu. Funkce zastaví čtení vstupního řetězce u prvního znaku, který nebude rozpoznán jako část čísla. Tento znak může být znak null ('\0' nebo L '\0') řetězce se ukončuje.

*Str* argument **atof –** a **_wtof –** má následující formát:

[*prázdné znaky*] [*přihlašování*] [*číslic*] [__.__ *číslic*] [{**e** &#124; **E** } [*přihlašování*]*číslic*]

A *prázdné znaky* se skládá ze znaků mezera nebo tabulátor, které jsou ignorovány; *přihlašování* je buď plus (+) nebo minus (-); a *číslic* jsou jeden nebo více desítkových číslic. Pokud se nezobrazí žádné číslic od desetinné čárky, alespoň číslice se musí nacházet za desetinnou čárkou. Může být následován desítkových číslic exponentu, které se skládají z úvodního písmene (**e**, nebo **E**) a volitelně podepsaný desítkové celé číslo.

UCRT verze těchto funkcí nepodporuje převod až po Fortran – vizuální styl (**d** nebo **D**) exponentu písmena. Toto nestandardní rozšíření je podporován v předchozích verzích CRT a může být k zásadní změně vašeho kódu.

Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají *národní prostředí* předán parametr namísto aktuálního národního prostředí.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof –**|**atof –**|**atof –**|**_wtof**|
|**_ttof –**|**atof –**|**atof –**|**_wtof**|

## <a name="requirements"></a>Požadavky

|Routine(s)|Požadovaný hlavičkový soubor|
|------------------|---------------------|
|**atof –**, **_atof_l –**|C: \<math.h > nebo \<stdlib.h > C++: \<cstdlib – >, \<stdlib.h >, \<cmath > nebo \<math.h >|
|**_wtof –**, **_wtof_l –**|C: \<stdlib.h > nebo \<wchar.h > C++: \<cstdlib – >, \<stdlib.h > nebo \<wchar.h >|

## <a name="example"></a>Příklad

Tento program ukazuje, jak lze převést čísel uložených jako řetězce na číselné hodnoty pomocí **atof –** a **_atof_l –** funkce.

```C
// crt_atof.c
//
// This program shows how numbers stored as
// strings can be converted to numeric
// values using the atof and _atof_l functions.

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function
    // using leading and training spaces.
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function
    // using the 'E' exponential formatting keyword.
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions
    // using the 'e' exponential formatting keyword
    // and showing different decimal point interpretations.
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}
```

```Output
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25
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
