---
title: _strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l
ms.date: 11/04/2016
apiname:
- _strtoi64
- _strtoi64_l
- _wcstoi64_l
- _wcstoi64
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
- _strtoi64
- strtoi64
- _stroi64_l
- _wcstoi64_l
- wcstoi64_l
- _wcstoi64
- wcstoi64
- strtoi64_l
helpviewer_keywords:
- _strtoi64 function
- _wcstoi64 function
- _strtoi64_l function
- string conversion, to integers
- _wcstoi64_l function
- strtoi64_l function
- wcstoi64 function
- strtoi64 function
- wcstoi64_l function
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
ms.openlocfilehash: a8097a31ebbc56281008f14da58671d5b2e4e8b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490776"
---
# <a name="strtoi64-wcstoi64-strtoi64l-wcstoi64l"></a>_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l

Převést řetězec **__int64** hodnotu.

## <a name="syntax"></a>Syntaxe

```C
__int64 _strtoi64(
   const char *strSource,
   char **endptr,
   int base
);
__int64 _wcstoi64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
__int64 _strtoi64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
__int64 _wcstoi64_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Řetězec zakončený hodnotou Null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví skenování.

*base*<br/>
Základna čísla pro použití.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_strtoi64 –** vrátí hodnotu představovanou řetězcem *strSource*s výjimkou případů, kdy reprezentace by způsobila přetečení, v takovém případě ji vrátí **_I64_MAX** nebo **_I64 _MIN**. Funkce vrátí 0, pokud žádné převody nemohou být provedeny. **_wcstoi64 –** vrátí hodnoty analogicky k **strtoi64 –**.

**_I64_MAX** a **_I64_MIN** jsou definovány v omezení. H.

Pokud *strSource* je **NULL** nebo *základní* je nenulový a menší než 2 nebo větší než 36, **errno** je nastavena na **EINVAL** .

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódů.

## <a name="remarks"></a>Poznámky

**_Strtoi64 –** funkce převede *strSource* do **__int64**. Obě funkce zastaví čtení řetězce *strSource* u prvního znaku, který nebude rozpoznán jako část čísla. Může to být ukončující znak null nebo první číselný znak větší než nebo rovna hodnotě může být *základní*. **_wcstoi64 –** je verze širokého znaku **_strtoi64 –**; její *strSource* argument je širokoznaký řetězec. Tyto funkce chovají identicky jinak.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoi64**|**_strtoi64**|**_strtoi64**|**_wcstoi64**|
|**_tcstoi64_l**|**_strtoi64_l**|**_strtoi64_l**|**_wcstoi64_l**|

Národního prostředí **LC_NUMERIC** kategorie určuje rozpoznávání znaku radix v *strSource **;* Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md). Funkce bez přípony _l používají aktuální národní prostředí; **_strtoi64_l –** a **_wcstoi64_l –** jsou stejné pro odpovídající funkce bez **_l** přípony s tím rozdílem, že používají předané národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování, je uložen v umístění, na které odkazuje *endptr*. Pokud žádné převody nemohou být provedeny (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložen v umístění, na které odkazuje *endptr*.

**_strtoi64 –** očekává, že *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

> [*prázdné znaky*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*číslic* &#124; *písmena*]  

A *prázdné znaky* může skládat ze znaků mezera a tabulátor, které jsou ignorovány; *číslic* jsou jeden nebo více desítkových číslic; *písmena* jsou jedno nebo více písmen "a" až "z" (nebo "A" až "Z").  První znak, který není vhodná pro tento formulář zastaví skenování. Pokud *základní* je mezi 2 a 36, je použit jako základ pro číslo. Pokud *základní* je 0, počáteční znaky řetězce odkazované *strSource* slouží ke stanovení základu. Pokud je první znak 0 a druhý znak není "x" nebo "X", řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak "0" a druhý znak je písmeno "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; jenom písmena, jejichž přiřazené hodnoty jsou menší než *základní* nejsou povoleny. První znak mimo rozsah základny zastaví skenování. Například pokud *základní* je 0 a první znak zkontrolovat je "0", předpokládá se osmičkové celé číslo a znak "8" nebo "9" zastaví skenování.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strtoi64 –**, **_strtoi64_l –**|\<stdlib.h>|
|**_wcstoi64 –**, **_wcstoi64_l –**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce převodu řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
