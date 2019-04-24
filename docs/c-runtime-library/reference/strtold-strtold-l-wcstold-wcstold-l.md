---
title: strtold, _strtold_l, wcstold, _wcstold_l
ms.date: 04/05/2018
apiname:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
ms.openlocfilehash: dcf1eca5b163c8553b43d747d53537ec424a793c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269186"
---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold, _strtold_l, wcstold, _wcstold_l

Převede řetězce na hodnotu long dvojité přesnosti s plovoucí desetinnou čárkou.

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
Řetězec zakončený hodnotou Null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví skenování.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtold** vrátí hodnotu čísla s plovoucí desetinnou čárkou jako **dlouhé** **double**, s výjimkou případů, kdy by reprezentace způsobila přetečení – v takovém případě funkce vrátí +/-**HUGE_VALL**. Znaménko **HUGE_VALL** odpovídá znaménku hodnoty, kterou nejde reprezentovat. **strtold** vrátí hodnotu 0, pokud převod lze provést nebo dochází k podtečení.

**wcstold** vrátí hodnoty analogicky k **strtold**. U obou funkcí **errno** je nastavena na **ERANGE** Pokud dojde k přetečení nebo podtečení a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Další informace o návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá funkce převede vstupní řetězec *strSource* k **dlouhé** **double**. **Strtold** funkce zastaví čtení řetězce *strSource* u prvního znaku, který nebude rozpoznán jako část čísla. Může to být ukončující znak null. Širokoznaká verze **strtold** je **wcstold**; její *strSource* argument je širokoznaký řetězec. Jinak tyto funkce chovají identicky.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

**LC_NUMERIC** kategorie aktuálního národního prostředí určuje rozpoznávání znaku radix v *strSource*. Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). Funkce bez **_l** přípona používají aktuální národní prostředí; **_strtold_l** a **_wcstold_l** jsou stejné jako **_strtold** a **_wcstold** s tím rozdílem, že místo toho používají národní prostředí, která Předaný. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování, je uložen na umístění, které ukazuje *endptr*. Pokud žádné převody nemohou být provedeny (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložen v umístění, které ukazuje *endptr*.

**strtold** očekává, že *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

[*prázdné znaky*] [*přihlašování*] [*číslic*] [. *číslice*] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*přihlašování* ]*číslic*]

A *prázdné znaky* může skládat ze znaků mezera a tabulátor, které jsou ignorovány; *přihlašování* je buď plus (**+**) nebo minus (**-**); a *číslic* jsou jeden nebo více desítkových číslic. Pokud se před číselnou soustavou znaků se nezobrazí žádné číslice, alespoň číslice se musí nacházet za číselnou soustavou znaků. Může být následován desítkových číslic exponentu, které se skládají z úvodního písmene (**d**, **D**, **e**, nebo **E**) a volitelně celé číslo se znaménkem. Pokud se nezobrazí část ani Číselná soustava znaků, považován za Číselná soustava znaků postupuje podle poslední číslice v řetězci. První znak, který není vhodná pro tento formulář zastaví skenování.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
