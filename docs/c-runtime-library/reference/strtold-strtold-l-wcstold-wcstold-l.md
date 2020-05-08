---
title: strtold, _strtold_l, wcstold, _wcstold_l
ms.date: 4/2/2020
api_name:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
- _o__strtold_l
- _o__wcstold_l
- _o_strtold
- _o_wcstold
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
ms.openlocfilehash: ba57eed25fd8e1310b9e837c55cb1e1f7ec2b718
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912603"
---
# <a name="strtold-_strtold_l-wcstold-_wcstold_l"></a>strtold, _strtold_l, wcstold, _wcstold_l

Převede řetězce na hodnotu typu Long s dvojitou přesností s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
long double strtold(
   const char *strSource,
   char **endptr
);
long double _strtold_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
long double wcstold(
   const wchar_t *strSource,
   wchar_t **endptr
);
long double wcstold_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Řetězec zakončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví skenování.

*locale*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtold** vrátí hodnotu čísla s plovoucí desetinnou čárkou jako typ **Long** **Double**, s výjimkou případů, kdy by reprezentace způsobila přetečení – v takovém případě funkce vrátí hodnotu +/-**HUGE_VALL**. Znaménko **HUGE_VALL** odpovídá znaménku hodnoty, kterou nelze reprezentovat. **strtold** vrátí hodnotu 0, pokud převod nelze provést, nebo dojde k podtečení.

**wcstold** vrací hodnoty obdobně **strtold**. Pro obě funkce je **errno** nastaveno na **ERANGE** , pokud dojde k přetečení nebo podtečení a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md).

Další informace o návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá funkce převede vstupní řetězec *strSource* na typ **Long** **Double**. Funkce **strtold** zastaví čtení řetězce *strSource* u prvního znaku, který nelze rozpoznat jako součást čísla. Může to být ukončující znak null. Verze **strtold** s velkým znakem je **wcstold**; jeho argument *strSource* je řetězec s velkým znakem. V opačném případě se tyto funkce chovají identicky.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

Nastavení kategorie **LC_NUMERIC** aktuálního národního prostředí Určuje rozpoznávání znaku základu v *strSource*. Další informace naleznete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkce bez přípony **_l** používají aktuální národní prostředí; **_strtold_l** a **_wcstold_l** jsou stejné jako **_strtold** a **_wcstold** s tím rozdílem, že místo toho používají národní prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **null**, ukazatel na znak, který zastavil skenování, je uložen v umístění, na které ukazuje *endptr*. Pokud převod nelze provést (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložena v umístění, na které odkazuje *endptr*.

**strtold** očekává, že *strSource* odkazuje na řetězec v následujícím tvaru:

[*prázdné znaky*] [*Sign*] [*číslice*] [. *číslice*] [{**d** &#124; **d** &#124; **e** &#124; **e**} [*Sign*]*číslice*]

*Mezera se může skládat* z mezer a znaků tabulátoru, které jsou ignorovány; *znaménko* je buď znaménko plus (**+**)**-** nebo mínus (); a *číslice* jsou jednu nebo více desítkových číslic. Pokud se před znakem základu neobjeví žádné číslice, musí se alespoň jedna objevit za znakem základu. V desítkových číslicích může následovat exponent, který se skládá z úvodního písmene (**d**, **d**, **e**nebo **e**) a volitelně podepsaného celého čísla. Pokud se nezobrazí část exponentu ani číselný znak, předpokládá se, že za poslední číslicí v řetězci bude následovat znak základu. První znak, který se nevejde do tohoto formuláře zastaví kontrolu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<Stdlib. h>|
|**wcstold**, **_wcstold_l**|\<Stdlib. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strtold.c
// Build with: cl /W4 /Tc crt_strtold.c
// This program uses strtold to convert a
// string to a long double-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   long double x;

   string = "3.1415926535898This stopped it";
   x = strtold(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtold = %.13Lf\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.1415926535898This stopped it
   strtold = 3.1415926535898
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Funkce řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
