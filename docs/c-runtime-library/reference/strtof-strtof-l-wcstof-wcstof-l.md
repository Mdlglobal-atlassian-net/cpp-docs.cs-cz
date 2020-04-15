---
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 4/2/2020
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
- _o__strtof_l
- _o__wcstof_l
- _o_strtof
- _o_wcstof
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
ms.openlocfilehash: f61aa0edeadd74a254f906dd745e18b059da7f24
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365136"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof, _strtof_l, wcstof, _wcstof_l

Převede řetězce na hodnotu s plovoucí desetinnou hodnotou s jednou přesností.

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
Řetězec ukončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví prohledávací.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtof** vrátí hodnotu čísla s plovoucí desetinnou desetinnou, s výjimkou případů, kdy by reprezentace způsobila přetečení, v takovém případě funkce vrátí +/-**HUGE_VALF**. Znaménko **HUGE_VALF** odpovídá znaménko hodnoty, které nelze reprezentovat. **strtof** vrátí 0, pokud nelze provést žádný převod nebo dojde k podtečení.

**wcstof** vrací hodnoty analogicky **k strtof**. Pro obě funkce je **errno** nastaveno na **ERANGE,** pokud dojde k přetečení nebo podtečení a je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

Další informace o návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá funkce převede vstupní řetězec *strSource* na **float**. Funkce **strtof** převede *strSource* na hodnotu s jednou přesností. **strtof** zastaví čtení řetězce *strSource* na první znak, který nelze rozpoznat jako součást čísla. To může být ukončující znak null. **wcstof** je širokoznaková verze **strtof**; jeho *argument strSource* je řetězec s širokým znakem. V opačném případě se tyto funkce chovají stejně.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof řekl:**|**strtof řekl:**|**wcstof řekl:**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

Nastavení **kategorie LC_NUMERIC** aktuálního národního prostředí určuje rozpoznání znaku radix v *strSource*; Další informace naleznete [v tématu setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkce, které nemají **příponu _l** používají aktuální národní prostředí; ty, které mají příponu jsou identické s tím rozdílem, že používají národní prostředí, které je předáno místo. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování je uložen v umístění, které je odkazuje *na endptr*. Pokud nelze provést žádný převod (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložena v umístění, na které je odkazováno *endptr*.

**strtof** očekává *strSource* přejděte na řetězec následujícího formuláře:

[*mezery*] [*znamení*] [*číslice*] [__.__ *číslice*] [{**e** &#124; **E**} [*znak*] *číslice*]

*Prázdné znaky* se mohou skládat z mezer a znaků tabulátoru, které jsou ignorovány; *znak* je buď**+** plus (**-**) nebo mínus ( ); a *číslice* jsou jedno nebo více desetinných míst. Pokud se před znakem radix neobjeví žádné číslice, musí se za znakem radix objevit alespoň jedna. Desetinná číslice mohou být následovány exponentem, který se skládá z úvodního písmene (**e** nebo **E**) a volitelně podepsaného celého čísla. Pokud se nezobrazí exponentní díl ani znak radix, předpokládá se, že znak radix následuje za poslední číslicí v řetězci. První znak, který se nevejde do tohoto formuláře zastaví skenování.

Verze těchto funkcí UCRT nepodporují převod exponentních písmen ve stylu Fortran (**d** nebo **D).** Toto nestandardní rozšíření bylo podporováno staršími verzemi CRT a může být narušující změnou pro váš kód.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C: \<stdlib.h> C++: &lt;cstdlib> nebo \<stdlib.h>|
|**wcstof**, **_wcstof_l**|C: \<stdlib.h \<> nebo wchar.h &lt;> C++: \<cstdlib>, stdlib.h> nebo \<wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Funkce řetězec na číselnou hodnotu](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
