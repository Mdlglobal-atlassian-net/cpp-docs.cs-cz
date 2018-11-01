---
title: strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l
ms.date: 11/04/2016
apiname:
- wcstoimax
- _wcstoimax_l
- _strtoimax_l
- strtoimax
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
- wcstoimax
- _tcstoimax
- strtoimax
- _wcstoimax_l
- _strtoimax_l
- _tcstoimax_l
helpviewer_keywords:
- strtoimax funciton
- conversion functions
- _strtoimax_l function
- _wcstoimax_l function
- wcstoimax function
ms.assetid: 4530d3dc-aaac-4a76-b7cf-29ae3c98d0ae
ms.openlocfilehash: e0a320f90b2c0f8653109a6ae0056c4c0cdd7455
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578149"
---
# <a name="strtoimax-strtoimaxl-wcstoimax-wcstoimaxl"></a>strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l

Převede řetězec na celočíselnou hodnotu největšího typu celé číslo se znaménkem podporované.

## <a name="syntax"></a>Syntaxe

```C
intmax_t strtoimax(
   const char *strSource,
   char **endptr,
   int base
);
intmax_t wcstoimax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
intmax_t _strtoimax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
intmax_t _wcstoimax_l(
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

**strtoimax** vrátí hodnotu, která představuje řetězec *strSource*, s výjimkou případů, kdy by reprezentace způsobila přetečení – v takovém případě vrátí **INTMAX_MAX** nebo **INTMAX_MIN**, a **errno** je nastavena na **ERANGE**. Funkce vrátí hodnotu 0, pokud žádné převody nemohou být provedeny. **wcstoimax –** vrátí hodnoty analogicky k **strtoimax**.

**INTMAX_MAX** a **INTMAX_MIN** jsou definovány v stdint.h.

Pokud *strSource* je **NULL** nebo *základní* je nenulový a menší než 2 nebo větší než 36, **errno** je nastavena na **EINVAL** .

Další informace o návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**Strtoimax** funkce převede *strSource* do **intmax_t**. Širokoznaká verze **strtoimax** je **wcstoimax –**; její *strSource* argument je širokoznaký řetězec. Jinak tyto funkce chovají identicky. Obě funkce zastaví čtení řetězce *strSource* u prvního znaku, který nebude rozpoznán jako část čísla. Může to být ukončující znak null nebo první číselný znak, který je větší než nebo rovna hodnotě může být *základní*.

Národního prostředí **LC_NUMERIC** kategorie určuje rozpoznávání znaku radix v *strSource*; Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). Funkce, které nemají **_l** přípona používají aktuální národní prostředí; **_strtoimax_l –** a **_wcstoimax_l –** jsou stejné pro odpovídající funkce, které nemají **_l** s tím rozdílem, že místo toho používají národní prostředí, která Předaný. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování, je uložen na umístění, které ukazuje *endptr*. Pokud žádné převody nemohou být provedeny (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložen v umístění, které ukazuje *endptr*.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoimax**|**strtoimax**|**strtoimax**|**wcstoimax –**|
|**_tcstoimax_l**|**strtoimax_l**|**_strtoimax_l**|**_wcstoimax_l**|

**strtoimax** očekává, že *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

> [*prázdné znaky*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*číslic* &#124; *písmena*]  

A *prázdné znaky* může skládat ze znaků mezera a tabulátor, které jsou ignorovány; *číslic* jsou jeden nebo více desítkových číslic; *písmena* jsou jedno nebo více písmen "a" až "z" (nebo "A" až "Z"). První znak, který není vhodná pro tento formulář zastaví skenování. Pokud *základní* je mezi 2 a 36, je použit jako základ pro číslo. Pokud *základní* je 0, počáteční znaky řetězce odkazované *strSource* slouží ke stanovení základu. Pokud je první znak "0" a druhý znak není "x" nebo "X", řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak "0" a druhý znak je písmeno "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; jenom písmena, jejichž přiřazené hodnoty jsou menší než *základní* nejsou povoleny. První znak mimo rozsah základny zastaví skenování. Například pokud *základní* je 0 a první znak zkontrolovat je "0", předpokládá se osmičkové celé číslo a znak "8" nebo "9" zastaví skenování.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoimax**, **_strtoimax_l –**, **wcstoimax –**, **_wcstoimax_l –**|\<inttypes.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce převodu řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l](strtoumax-strtoumax-l-wcstoumax-wcstoumax-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
