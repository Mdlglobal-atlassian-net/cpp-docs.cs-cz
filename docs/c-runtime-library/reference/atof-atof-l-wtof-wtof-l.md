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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 492719a0cc0f8ac079b257ec8d7aa1014c5b2a86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348924"
---
# <a name="atof-_atof_l-_wtof-_wtof_l"></a>atof, _atof_l, _wtof, _wtof_l

Převeďte řetězec na double.

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

*Str*<br/>
Řetězec, který má být převeden.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí **dvojitou** hodnotu vytvořenou interpretací vstupních znaků jako čísla. Vrácená hodnota je 0,0, pokud vstup nelze převést na hodnotu tohoto typu.

Ve všech případech mimo rozsah je **errno** nastaveno na **ERANGE**. Pokud je předaný parametr **null**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce nastavit **errno** **eINVAL** a vrátit 0.

## <a name="remarks"></a>Poznámky

Tyto funkce převést řetězec znaku na double-přesnost, s plovoucí desetinnou hodnotou.

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako číselnou hodnotu zadaného typu. Funkce zastaví čtení vstupního řetězce na první znak, který nelze rozpoznat jako součást čísla. Tento znak může být znak emitující řetězec nulovým znakem (\0 nebo L'\0).

*Argument str* to **atof** a **_wtof** má následující podobu:

[*mezery*] [*znamení*] [*číslice*] [__.__ *číslice*] [**{ e** &#124; **E** }[*znaménko*]*číslice*]

*Prázdné znaky* se skládají z mezer nebo tabulátoru znaků, které jsou ignorovány; *znak* je buď plus (+) nebo mínus (-); a *číslice* jsou jedno nebo více desetinných míst. Pokud se před desetinnou čárkou neobjeví žádné číslice, musí se za desetinnou čárkou objevit alespoň jedna. Desetinná číslice mohou být následovány exponentem, který se skládá z úvodního písmene (**e**, nebo **E**) a volitelně podepsaného desetinného celého čísla.

Verze těchto funkcí UCRT nepodporují převod exponentních písmen ve stylu Fortran (**d** nebo **D).** Toto nestandardní rozšíření bylo podporováno staršími verzemi CRT a může být narušující změnou pro váš kód.

Verze těchto funkcí s **příponou _l** jsou identické s tím rozdílem, že používají parametr *národního prostředí* předaný namísto aktuálního národního prostředí.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**Atof**|**Atof**|**_wtof**|
|**_ttof**|**Atof**|**Atof**|**_wtof**|

## <a name="requirements"></a>Požadavky

|Rutina (y)|Požadovaný hlavičkový soubor|
|------------------|---------------------|
|**atof**, **_atof_l**|C: \<math.h \<> nebo stdlib.h \<> C++: \<cstdlib>, stdlib.h>, \<cmath> nebo \<math.h>|
|**_wtof** **_wtof_l**|C: \<stdlib.h \<> nebo wchar.h \<> C++: \<cstdlib>, stdlib.h> nebo \<wchar.h>|

## <a name="example"></a>Příklad

Tento program ukazuje, jak mohou být čísla uložená jako řetězce převedena na číselné hodnoty pomocí funkcí **atof** a **_atof_l.**

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
[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
