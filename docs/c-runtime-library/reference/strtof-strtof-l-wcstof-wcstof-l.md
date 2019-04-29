---
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 04/05/2018
apiname:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
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
ms.openlocfilehash: 10a50a175685f3e8f7f1241683c7705fd9a9b142
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376429"
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof, _strtof_l, wcstof, _wcstof_l

Převede řetězce na hodnotu s plovoucí desetinnou čárkou jednoduchou přesností.

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
Řetězec zakončený hodnotou Null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví skenování.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtof** vrátí hodnotu čísla s plovoucí desetinnou čárkou, s výjimkou případů, kdy by reprezentace způsobila přetečení, ve kterém takovém případě funkce vrátí +/-**HUGE_VALF**. Znaménko **HUGE_VALF** odpovídá znaménku hodnoty, kterou nejde reprezentovat. **strtof** vrátí hodnotu 0, pokud převod lze provést nebo dochází k podtečení.

**wcstof** vrátí hodnoty analogicky k **strtof**. U obou funkcí **errno** je nastavena na **ERANGE** Pokud dojde k přetečení nebo podtečení a je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Další informace o návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá funkce převede vstupní řetězec *strSource* k **float**. **Strtof** funkce převede *strSource* na hodnotu jednoduchou přesností. **strtof** zastaví čtení řetězce *strSource* u prvního znaku, který nebude rozpoznán jako část čísla. Může to být ukončující znak null. **wcstof** je verze širokého znaku **strtof**; její *strSource* argument je širokoznaký řetězec. Jinak tyto funkce chovají identicky.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

**LC_NUMERIC** kategorie aktuálního národního prostředí určuje rozpoznávání znaku radix v *strSource*; Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). Funkce, které nemají **_l** přípona používají aktuální národní prostředí; ty, které mají příponu jsou stejné s tím rozdílem, že používají národní prostředí, které je předáno místo. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování, je uložen na umístění, které ukazuje *endptr*. Pokud žádné převody nemohou být provedeny (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložen v umístění, které ukazuje *endptr*.

**strtof** očekává, že *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

[*prázdné znaky*] [*přihlašování*] [*číslic*] [__.__ *číslic*] [{**e** &#124; **E**} [*přihlašování*] *číslic*]

A *prázdné znaky* může skládat ze znaků mezera a tabulátor, které jsou ignorovány; *přihlašování* je buď plus (**+**) nebo minus (**-**); a *číslic* jsou jeden nebo více desítkových číslic. Pokud se před číselnou soustavou znaků se nezobrazí žádné číslice, alespoň číslice se musí nacházet za číselnou soustavou znaků. Může být následován desítkových číslic exponentu, které se skládají z úvodního písmene (**e** nebo **E**) a volitelného znaménka. Pokud se nezobrazí část ani Číselná soustava znaků, považován za Číselná soustava znaků postupuje podle poslední číslice v řetězci. První znak, který není vhodná pro tento formulář zastaví skenování.

UCRT verze těchto funkcí nepodporuje převod až po Fortran – vizuální styl (**d** nebo **D**) exponentu písmena. Toto nestandardní rozšíření je podporován v předchozích verzích CRT a může být k zásadní změně vašeho kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C: \<stdlib.h > C++: &lt;cstdlib – > nebo \<stdlib.h >|
|**wcstof**, **_wcstof_l**|C: \<stdlib.h > nebo \<wchar.h > C++: &lt;cstdlib – >, \<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
