---
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 04/05/2018
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: b2b2e7d230074b5a464260d36b41c28b9951d65b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957754"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof, _strtof_l, wcstof, _wcstof_l

Převede řetězce na hodnotu s jednoduchou přesností s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>Parametry

*strSource*<br/>
Řetězec zakončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví skenování.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtof** vrací hodnotu čísla s plovoucí desetinnou čárkou, s výjimkou případů, kdy by reprezentace způsobila přetečení. v takovém případě funkce vrací hodnotu +/-**HUGE_VALF**. Znaménko **HUGE_VALF** odpovídá znaménku hodnoty, kterou nelze reprezentovat. **strtof** vrátí hodnotu 0, pokud převod nelze provést, nebo dojde k podtečení.

**wcstof** vrací hodnoty obdobně **strtof**. Pro obě funkce je **errno** nastaveno na **ERANGE** , pokud dojde k přetečení nebo podtečení a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Další informace o návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá funkce převede vstupní řetězec *strSource* na typ **float**. Funkce **strtof** převede *strSource* na hodnotu s jednoduchou přesností. **strtof** zastaví čtení řetězce *strSource* u prvního znaku, který nelze rozpoznat jako součást čísla. Může to být ukončující znak null. **wcstof** je **strtof**verze s velkým znakem; jeho argument *strSource* je řetězec s velkým znakem. V opačném případě se tyto funkce chovají identicky.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

Nastavení kategorie **LC_NUMERIC** aktuálního národního prostředí Určuje rozpoznávání znaku základu v *strSource*; Další informace naleznete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkce, které nemají příponu **_l** , používají aktuální národní prostředí; ty, které mají příponu, jsou stejné s tím rozdílem, že místo toho používají národní prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **null**, ukazatel na znak, který zastavil skenování, je uložen v umístění, na které ukazuje *endptr*. Pokud převod nelze provést (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložena v umístění, na které odkazuje *endptr*.

**strtof** očekává, že *strSource* odkazuje na řetězec v následujícím tvaru:

[*prázdné znaky*] [*Sign*] [*číslice*] [ __.__ *číslice*] [{**e** &#124; **e**} [*Sign*] *číslice*]

*Mezera se může skládat* z mezer a znaků tabulátoru, které jsou ignorovány; *znaménko* je buď znaménko plus ( **+** ), nebo mínus ( **-** ); a *číslice* jsou jedna nebo více desítkových číslic. Pokud se před znakem základu neobjeví žádné číslice, musí se alespoň jedna objevit za znakem základu. V desítkových číslicích může následovat exponent, který se skládá z úvodního písmene (**e** nebo **e**) a volitelně podepsaného celého čísla. Pokud se nezobrazí část exponentu ani číselný znak, předpokládá se, že za poslední číslicí v řetězci bude následovat znak základu. První znak, který se nevejde do tohoto formuláře zastaví kontrolu.

Verze UCRT těchto funkcí nepodporují konverzi exponentů pro styl FORTRAN (**d** nebo **d**). Toto nestandardní rozšíření bylo podporováno staršími verzemi CRT a může být zásadní změnou kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C: \<Stdlib. h > C++: &lt;cstdlib > nebo \<Stdlib. h >|
|**wcstof**, **_wcstof_l**|C: \<Stdlib. h > nebo \<WCHAR. h > C++: &lt;cstdlib >, \<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Funkce převodu řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
