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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 9acc98296651f549ceffb1e1deab350a71747ea5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365367"
---
# <a name="strtold-_strtold_l-wcstold-_wcstold_l"></a>strtold, _strtold_l, wcstold, _wcstold_l

Převede řetězce na dlouhou hodnotu s dvojitou přesností s plovoucí desetinnou desetinnou hodnotou.

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
Řetězec ukončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví prohledávací.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtold** vrátí hodnotu čísla s plovoucí desetinnou desetinnou jako **dlouhou** **dvojitou**hodnotu , s výjimkou případů, kdy by reprezentace způsobila přetečení – v takovém případě funkce vrátí +/-**HUGE_VALL**. Znaménko **HUGE_VALL** odpovídá znaménko hodnoty, které nelze reprezentovat. **strtold** vrátí 0, pokud nelze provést žádný převod nebo dojde k podtečení.

**wcstold** vrací hodnoty analogicky k **strtold**. Pro obě funkce je **errno** nastaveno na **ERANGE,** pokud dojde k přetečení nebo podtečení a je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md).

Další informace o návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá funkce převede vstupní řetězec *strSource* na **dlouhou** **dvojitou**. Funkce **strtold** zastaví čtení řetězce *strSource* na prvním znaku, který nemůže rozpoznat jako součást čísla. To může být ukončující znak null. Širokoúhlá verze **strtold** je **wcstold**; jeho *argument strSource* je řetězec s širokým znakem. V opačném případě se tyto funkce chovají stejně.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold řekl:**|**strtold řekl:**|**wcstold řekl**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

Nastavení **kategorie LC_NUMERIC** aktuálního národního prostředí určuje rozpoznávání znaku radix v *strSource*. Další informace naleznete [v tématu setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkce bez **přípony _l** používají aktuální národní prostředí; **_strtold_l** a **_wcstold_l** jsou shodné s **_strtold** a **_wcstold** s tím rozdílem, že místo toho používají národní prostředí, které je předáno. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování je uložen v umístění, které je odkazuje *na endptr*. Pokud nelze provést žádný převod (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložena v umístění, na které je odkazováno *endptr*.

**strtold** očekává *strSource* přejděte na řetězec následujícího formuláře:

[*mezery*] [*znamení*] [*číslice*] [. *číslice*] [**{ d** &#124; **D** &#124; **e** &#124; **E**}[*znaménko*]*číslice*]

*Prázdné znaky* se mohou skládat z mezer a znaků tabulátoru, které jsou ignorovány; *znak* je buď**+** plus (**-**) nebo mínus ( ); a *číslice* jsou jedno nebo více desetinných míst. Pokud se před znakem radix neobjeví žádné číslice, musí se za znakem radix objevit alespoň jedna. Desetinná místa mohou být následována exponentem, který se skládá z úvodního písmene (**d**, **D**, **e**nebo **E**) a volitelně podepsaného celého čísla. Pokud se nezobrazí exponentní díl ani znak radix, předpokládá se, že znak radix následuje za poslední číslicí v řetězci. První znak, který se nevejde do tohoto formuláře zastaví skenování.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
