---
title: strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l
ms.date: 11/04/2016
api_name:
- wcstoimax
- _wcstoimax_l
- _strtoimax_l
- strtoimax
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
ms.openlocfilehash: ea1ab72a361987d0ccdfe1f4b4a4efb6a0fb427e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957665"
---
# <a name="strtoimax-_strtoimax_l-wcstoimax-_wcstoimax_l"></a>strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l

Převede řetězec na celočíselnou hodnotu největšího podporovaného typu celého čísla se znaménkem.

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
Řetězec zakončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví skenování.

*base*<br/>
Číselná základna, která se má použít.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtoimax** vrací hodnotu reprezentovanou v řetězci *strSource*, s výjimkou případů, kdy by reprezentace způsobila přetečení – v takovém případě vrátí **INTMAX_MAX** nebo **INTMAX_MIN**a **errno** je nastaven na **ERANGE** . Funkce vrátí hodnotu 0, pokud převod nelze provést. **wcstoimax** vrací hodnoty obdobně **strtoimax**.

**INTMAX_MAX** a **INTMAX_MIN** jsou definovány v stdin. h.

Pokud má StrSource **hodnotu null** nebo *základní* hodnota je nenulová a buď menší než 2, nebo větší než 36, **errno** je nastavena na hodnotu **EINVAL**.

Další informace o návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **strtoimax** převede *strSource* na **intmax_t**. Verze **strtoimax** s velkým znakem je **wcstoimax**; jeho argument *strSource* je řetězec s velkým znakem. V opačném případě se tyto funkce chovají identicky. Obě funkce přestanou číst řetězec *strSource* u prvního znaku, který nedokáže rozpoznat jako součást čísla. Může to být ukončující znak null nebo se může jednat o první číselný znak, který je větší nebo roven *základu*.

Nastavení kategorie **LC_NUMERIC** národního prostředí Určuje rozpoznávání znaku základu v *strSource*; Další informace naleznete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkce, které nemají příponu **_l** , používají aktuální národní prostředí; **_strtoimax_l** a **_wcstoimax_l** jsou stejné jako odpovídající funkce, které nemají příponu **_l** s tím rozdílem, že místo toho používají národní prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **null**, ukazatel na znak, který zastavil skenování, je uložen v umístění, na které ukazuje *endptr*. Pokud převod nelze provést (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložena v umístění, na které odkazuje *endptr*.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoimax**|**strtoimax**|**strtoimax**|**wcstoimax**|
|**_tcstoimax_l**|**strtoimax_l**|**_strtoimax_l**|**_wcstoimax_l**|

**strtoimax** očekává, že *strSource* odkazuje na řetězec v následujícím tvaru:

> [*prázdné znaky*] [{ **+** &#124; &#124; &#124; }] [0 [{x x}]] [číslice písmen] **-**

*Mezera se může skládat* z mezer a znaků tabulátoru, které jsou ignorovány; *číslice* jsou jednu nebo více desítkových číslic; *písmeny* jsou jedno nebo více písmen "a" až "z" (nebo "a" až "z"). První znak, který se nevejde do tohoto formuláře zastaví kontrolu. Pokud je *základ* mezi 2 a 36, použije se jako základ čísla. Pokud je *základ* 0, pro určení základu se použijí počáteční znaky řetězce, na který odkazuje *strSource* . Pokud je první znak 0 a druhý znak není x nebo X, řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak "0" a druhý znak je "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; povolena jsou pouze písmena, jejichž přiřazené hodnoty jsou menší než *Base* . První znak mimo rozsah základny zastaví skenování. Pokud je například *základ* 0 a první naskenovaný znak je "0", předpokládá se osmičkové celé číslo a znak "8" nebo "9" zastaví kontrolu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoimax**, **_strtoimax_l**, **wcstoimax**, **_wcstoimax_l**|\<inttypes.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
