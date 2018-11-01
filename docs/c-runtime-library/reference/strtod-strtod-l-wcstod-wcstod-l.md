---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 10/20/2017
apiname:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
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
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: c8c2b3b491e2e7265829fa88580529dc757ace8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469326"
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod, _strtod_l, wcstod, _wcstod_l

Převod řetězců na hodnoty dvojitou přesností.

## <a name="syntax"></a>Syntaxe

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
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

**strtod** vrátí hodnotu čísla s plovoucí desetinnou čárkou, s výjimkou případů, kdy by reprezentace způsobila přetečení, ve kterém takovém případě funkce vrátí +/-**HUGE_VAL**. Znaménko **HUGE_VAL** odpovídá znaménku hodnoty, kterou nejde reprezentovat. **strtod** vrátí hodnotu 0, pokud převod lze provést nebo dochází k podtečení.

**wcstod –** vrátí hodnoty analogicky k **strtod**. U obou funkcí **errno** je nastavena na **ERANGE** Pokud dojde k přetečení nebo podtečení a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o tomto a dalších návratových kódech.

## <a name="remarks"></a>Poznámky

Každá funkce převede vstupní řetězec *strSource* k **double**. **Strtod** funkce převede *strSource* na hodnotu s dvojitou přesností. **strtod** zastaví čtení řetězce *strSource* u prvního znaku, který nebude rozpoznán jako část čísla. Může to být ukončující znak null. **wcstod –** je verze širokého znaku **strtod**; její *strSource* argument je širokoznaký řetězec. Tyto funkce chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod –**|**strtod**|**strtod**|**wcstod –**|
|**_tcstod_l –**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

**LC_NUMERIC** kategorie aktuálního národního prostředí určuje rozpoznávání znaku radix bodu v *strSource*. Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md). Funkce bez **_l** přípona používají aktuální národní prostředí; **_strtod_l –** je stejný jako **_strtod_l –** s tím rozdílem, že používají *národní prostředí* místo něho předán. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování, je uložen v umístění, na které odkazuje *endptr*. Pokud žádné převody nemohou být provedeny (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložen v umístění, na které odkazuje *endptr*.

**strtod** očekává, že *strSource* tak, aby odkazoval na řetězec z jedné z následujících forem:

[*prázdné*] [*přihlašovací*] {*číslic* [*základ –* *číslic*] &#124;  *základ –* *číslic*} [{**e** &#124; **E**} [*přihlašovací*] *číslic*] [*prázdné*] [*přihlašovací*] {**0 x** &#124; **0 X**} {*hexdigits* [ *základ –* *hexdigits*] &#124; *základ –* *hexdigits*} [{**p** &#124; **P**} [*přihlašovací*] *hexdigits*] [*prázdné*] [*přihlašovací*] { **INF** &#124; **INFINITY**} [*prázdné*] [*přihlašovací*]  **NAN** [*pořadí*]

Volitelný úvodní *prázdné znaky* může skládat ze znaků mezera a tabulátor, které jsou ignorovány; *přihlašování* je buď plus (+) nebo minus (-); *číslic* jsou jeden nebo více desítkových číslic; *hexdigits* jsou jednoho nebo několika šestnáctkovými číslicemi; *základ číselné soustavy* je číselnou soustavou znaků bodu, buď tečku (.) v výchozí národní prostředí "C", nebo specifické pro národní prostředí hodnotu, pokud aktuální národní prostředí je jiné, nebo když *národní prostředí* určena; *pořadí* je posloupnost alfanumerické znaky nebo znaky podtržení. Ve formulářích decimal a šestnáctkové číslo Pokud žádné číslice se před číselnou soustavou znaků bodu, alespoň se musí nacházet za číselnou soustavou znaků bodu. Ve formuláři desítkové může následovat desítkových číslic exponentu, které se skládají z úvodního písmene (**e** nebo **E**) a volitelného znaménka. V šestnáctkovém formátu, může být následován šestnáctkových číslic exponentu, které se skládají z úvodního písmene (**p** nebo **P**) a volitelně šestnáctkové celé číslo se znaménkem, který představuje exponent jako mocninou čísla 2. V obou tvarech Pokud se nezobrazí část ani Číselná soustava znaků postupuje bod, bod Číselná soustava znaků se předpokládá, že podle poslední číslice v řetězci. V obou se ignoruje velikost písmen **INF** a **NAN** formuláře. První znak, který není vhodná pro jednu z těchto forem zastaví skenování.

UCRT verze těchto funkcí nepodporuje převod až po Fortran – vizuální styl (**d** nebo **D**) exponentu písmena. Toto nestandardní rozšíření je podporován v předchozích verzích CRT a může být k zásadní změně vašeho kódu. Verze UCRT podporují hexadecimálními řetězci a dopad na dobu odezvy INF a NAN hodnoty, které nejsou podporované v dřívějších verzích. Také to může způsobit změny způsobující chyby ve vašem kódu. Například by řetězců "0x1a" interpretovat **strtod** za 0,0 v předchozích verzích, ale jako 26.0 ve verzi UCRT.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtod**, **_strtod_l –**|C: &lt;stdlib.h > C++: &lt;cstdlib – > nebo &lt;stdlib.h > |
|**wcstod –**, **_wcstod_l –**|C: &lt;stdlib.h > nebo &lt;wchar.h > C++: &lt;cstdlib – >, &lt;stdlib.h > nebo &lt;wchar.h > |

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Funkce převodu řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
