---
title: strtof –, _strtof_l –, wcstof –, _wcstof_l – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95db2a75d04454289b01f96680df6c5b5ab89e78
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof –, _strtof_l –, wcstof –, _wcstof_l –

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
Řetězce ukončené hodnotou Null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví kontroly.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtof –** vrací hodnotu číslo s plovoucí desetinnou čárkou s výjimkou případů, kdy reprezentace by způsobilo přetečení, ve kterém případ funkce vrátí +/-**HUGE_VALF**. Znaménko **HUGE_VALF** odpovídá znaménko hodnotu, která není možné vyjádřit. **strtof –** vrátí hodnotu 0, pokud žádný převod můžete provést, nebo dojde podtečení.

**wcstof –** vrátí hodnot analogicky na **strtof –**. Pro obě funkce **errno** je nastaven na **erange –** Pokud dojde k přetečení nebo podtečení a volána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

Další informace o návratové kódy najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Jednotlivé funkce převede vstupní řetězec *strSource* k **float**. **Strtof –** funkce převede *strSource* na hodnotu jednoduchou přesností. **strtof –** ukončí čtení řetězce *strSource* u prvního znaku nemůže rozpoznat jako součást číslo. To může být ukončující znak hodnoty null. **wcstof –** je verze široká charakterová **strtof –**; jeho *strSource* je argumentem široká charakterová řetězce. Tyto funkce, jinak hodnota chovají stejně jako.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof –**|**strtof –**|**strtof –**|**wcstof –**|
|**_tcstof_l –**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

**Lc_numeric –** kategorie nastavení aktuální národní prostředí určuje rozpoznávání základ – znak v *strSource*; Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). Funkce, které nemají **_l** příponu použijte aktuální národní prostředí, ty, které se přípona jsou shodné s tím rozdílem, že používají národní prostředí, je předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavena kontroly je uložený v umístění, které ukazuje *endptr*. Pokud žádný převod lze provést (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základní), hodnota *strSource* je uložený v umístění, které ukazuje *endptr*.

**strtof –** očekává *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

[*prázdné*] [*přihlašovací*] [*číslic*] [__.__ *číslic*] [{**e** &#124; **E**} [*přihlašovací*] *číslic*]

A *prázdné* může obsahovat místa a karta znaků, které se mají ignorovat; *přihlašovací* je buď plus (**+**) nebo minus (**-**); a *číslic* jsou jeden nebo více desetinných míst. Pokud před základ – znak, který se zobrazí žádné číslice, alespoň jeden musí být uvedena za základ – znak. Desetinných míst může následovat exponentem, který se skládá z úvodní písmeno (**e** nebo **E**) a volitelně znaménkem. Pokud exponentu část ani základ – znak zobrazí, předpokládá se základ – znak podle poslední číslice v řetězci. První znak, který se nevejde tento formulář zastaví kontroly.

Verze UCRT tyto funkce nepodporuje převod Fortran stylu (**d** nebo **D**) exponentu písmena. Toto nestandardní rozšíření byl podporován ve starších verzích CRT a může být narušující změně kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtof –**, **_strtof_l –**|C: \<stdlib.h > C++: &lt;cstdlib – > nebo \<stdlib.h >|
|**wcstof –**, **_wcstof_l –**|C: \<stdlib.h > nebo \<wchar.h > C++: &lt;cstdlib – >, \<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

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
