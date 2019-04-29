---
title: strtoull, _strtoull_l, wcstoull, _wcstoull_l
ms.date: 11/04/2016
apiname:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
ms.openlocfilehash: f23799b43a356600f48fb0fbf32b4604966c416b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379204"
---
# <a name="strtoull-strtoulll-wcstoull-wcstoulll"></a>strtoull, _strtoull_l, wcstoull, _wcstoull_l

Převede řetězce na hodnotu unsigned long long integer.

## <a name="syntax"></a>Syntaxe

```C
unsigned long long strtoull(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long long _strtoull_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long long wcstoull(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long long _wcstoull_l(
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
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

**strtoull –** vrátí převedenou hodnotu, pokud existuje, nebo **ULLONG_MAX** při přetečení. **strtoull –** vrátí hodnotu 0, pokud žádné převody nemohou být provedeny. **wcstoull –** vrátí hodnoty analogicky k **strtoull –**. U obou funkcí **errno** je nastavena na **ERANGE** Pokud dojde k přetečení nebo podtečení.

Další informace o návratových kódech naleznete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí převede vstupní řetězec *strSource* do **bez znaménka** **dlouhé** **dlouhé** celočíselnou hodnotu.

**strtoull –** zastaví čtení řetězce *strSource* u prvního znaku, který nebude rozpoznán jako část čísla. Může to být ukončující znak null nebo první číselný znak, který je větší než nebo rovna hodnotě může být *základní*. Nastavení jazyka **LC_NUMERIC** kategorie národního prostředí určuje rozpoznávání znaku radix v *strSource*; Další informace najdete v tématu [setlocale _wsetlocale](setlocale-wsetlocale.md). **strtoull –** a **wcstoull –** používají aktuální národní prostředí; **_strtoull_l –** a **_wcstoull_l –** místo toho použijte národní prostředí, které je předáno, ale jsou identické jinak. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování, je uložen na umístění, které ukazuje *endptr*. Pokud žádné převody nemohou být provedeny (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložen v umístění, které ukazuje *endptr*.

**wcstoull –** je verze širokého znaku **strtoull –** a jeho *strSource* argument je širokoznaký řetězec. Jinak tyto funkce chovají identicky.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull –**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull –** očekává, že *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

> [*prázdné znaky*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*číslic* &#124; *písmena*]  

A *prázdné znaky* může skládat ze znaků mezera a tabulátor, které jsou ignorovány. *číslice* jsou jeden nebo více desítkových číslic. *písmena* jsou jedno nebo více písmen "a" až "z" (nebo "A" až "Z"). První znak, který není vhodná pro tento formulář zastaví skenování. Pokud *základní* je mezi 2 a 36, je použit jako základ pro číslo. Pokud *základní* je 0, počáteční znaky řetězce, který ukazuje *strSource* slouží ke stanovení základu. Pokud je první znak "0" a druhý znak není "x" nebo "X", řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak "0" a druhý znak je písmeno "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; jenom písmena, jejichž přiřazené hodnoty jsou menší než *základní* nejsou povoleny. První znak mimo rozsah základny zastaví skenování. Například pokud *základní* je 0 a první znak zkontrolovat je "0", předpokládá se osmičkové celé číslo a znak "8" nebo "9" zastaví skenování. **strtoull –** povoluje znaménko plus (**+**) nebo minus (**-**) předponu; úvodní znaménko mínus označuje, že návratová hodnota je negovat.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoull**|\<stdlib.h>|
|**wcstoull –**|\<stdlib.h > nebo \<wchar.h >|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce převodu řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
