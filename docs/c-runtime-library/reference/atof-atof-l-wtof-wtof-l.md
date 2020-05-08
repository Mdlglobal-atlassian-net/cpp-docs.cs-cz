---
title: atof, _atof_l, _wtof, _wtof_l
ms.date: 4/2/2020
api_name:
- _wtof_l
- atof
- _atof_l
- _wtof
- _o__atof_l
- _o__wtof
- _o__wtof_l
- _o_atof
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 5200b93a5745dfb8e9b31cd5663452b84cb3058a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909116"
---
# <a name="atof-_atof_l-_wtof-_wtof_l"></a>atof, _atof_l, _wtof, _wtof_l

Převeďte řetězec na hodnotu Double.

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

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí hodnotu typu **Double** vytvořenou interpretem vstupních znaků jako čísla. Návratová hodnota je 0,0, pokud vstup nelze převést na hodnotu daného typu.

V všech případech mimo rozsah je **errno** nastaveno na **ERANGE**. Pokud předaný parametr má **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Tyto funkce převádějí řetězec znaků na hodnotu s dvojitou přesností a plovoucí desetinnou čárkou.

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako číselnou hodnotu zadaného typu. Funkce zastaví čtení vstupního řetězce u prvního znaku, který nemůže rozpoznat jako součást čísla. Tento znak může být znak null (' \ 0 ' nebo L ' \ 0 ') ukončující řetězec.

Argument *str* pro **atof** a **_wtof** má následující tvar:

[*prázdné znaky*] [*Sign*] [*číslice*] [__.__ *číslice*] [{**e** &#124; **e** } [*Sign*]*číslice*]

*Mezera* se skládá z mezer nebo znaků tabulátoru, které jsou ignorovány; *znaménko* je buď znaménko plus (+) nebo minus (-); a *číslice* jsou jednu nebo více desítkových číslic. Pokud se před desetinnou čárkou neobjeví žádné číslice, musí se aspoň jedna objevit za desetinnou čárkou. Desítkové číslice mohou následovat exponent, který se skládá z úvodního písmene (**e**nebo **e**) a volitelně podepsaného desítkového čísla.

Verze UCRT těchto funkcí nepodporují konverzi exponentů pro styl FORTRAN (**d** nebo **d**). Toto nestandardní rozšíření bylo podporováno staršími verzemi CRT a může být zásadní změnou kódu.

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr *národního prostředí* namísto aktuálního národního prostředí.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>Požadavky

|Rutiny (y)|Požadovaný hlavičkový soubor|
|------------------|---------------------|
|**atof**, **_atof_l**|C: \<Math. h> nebo \<Stdlib. h> C++: \<cstdlib>, \<Stdlib. h>, \<cmath> nebo \<Math. h>|
|**_wtof** **_wtof_l**|C: \<Stdlib. h> nebo \<WCHAR. h> C++: \<cstdlib>, \<stdlib. h> nebo \<WCHAR. h>|

## <a name="example"></a>Příklad

Tento program ukazuje, jak mohou být čísla uložená jako řetězce převedeny na číselné hodnoty pomocí funkcí **atof** a **_atof_l** .

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
