---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
ms.date: 11/04/2016
apiname:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
ms.openlocfilehash: dec7debff809f8b3d61856f9be77bc590d845c12
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210754"
---
# <a name="strtoui64-wcstoui64-strtoui64l-wcstoui64l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

Převod řetězce na nepodepsaný **__int64** hodnotu.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
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

**_strtoui64 –** vrátí hodnotu představovanou řetězcem *strSource*s výjimkou případů, kdy reprezentace by způsobila přetečení, v takovém případě ji vrátí **_UI64_MAX**. **_strtoui64 –** vrátí hodnotu 0, pokud žádné převody nemohou být provedeny.

**_UI64_MAX** je definována v omezení. H.

Pokud *strSource* je **NULL** nebo *základní* je nenulový a menší než 2 nebo větší než 36, **errno** je nastavena na **EINVAL** .

Zobrazit [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Další informace o těchto a dalších návratových kódů.

## <a name="remarks"></a>Poznámky

**_Strtoui64 –** funkce převede *strSource* do **bez znaménka** **__int64**. **_wcstoui64 –** je verze širokého znaku **_strtoui64 –**; její *strSource* argument je širokoznaký řetězec. V opačném případě tyto funkce chovají identicky.

Obě funkce zastaví čtení řetězce *strSource* u prvního znaku, který nebude rozpoznán jako část čísla. Může to být ukončující znak null nebo první číselný znak větší než nebo rovna hodnotě může být *základní*.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

Aktuální národní prostředí **LC_NUMERIC** kategorie určuje rozpoznávání znaku radix v *strSource*; Další informace najdete v tématu [setlocale](setlocale-wsetlocale.md). Funkce bez přípony _l používají aktuální národní prostředí; **_strtoui64_l –** a **_wcstoui64_l –** jsou stejné pro odpovídající funkce bez **_l** přípony s tím rozdílem, že používají předané národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování, je uložen v umístění, na které odkazuje *endptr*. Pokud žádné převody nemohou být provedeny (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložen v umístění, na které odkazuje *endptr*.

**_strtoui64 –** očekává, že *strSource* tak, aby odkazoval na řetězec v následujícím formátu:

> [*prázdné znaky*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*číslic* &#124; *písmena*]  

A *prázdné znaky* může skládat ze znaků mezera a tabulátor, které jsou ignorovány. *číslice* jsou jeden nebo více desítkových číslic. *písmena* jsou jedno nebo více písmen "a" až "z" (nebo "A" až "Z"). První znak, který není vhodná pro tento formulář zastaví skenování. Pokud *základní* je mezi 2 a 36, je použit jako základ pro číslo. Pokud *základní* je 0, počáteční znaky řetězce odkazované *strSource* slouží ke stanovení základu. Pokud je první znak 0 a druhý znak není "x" nebo "X", řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak "0" a druhý znak je písmeno "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; jenom písmena, jejichž přiřazené hodnoty jsou menší než *základní* nejsou povoleny. První znak mimo rozsah základny zastaví skenování. Například pokud *základní* je 0 a první znak zkontrolovat je "0", předpokládá se osmičkové celé číslo a znak "8" nebo "9" zastaví skenování.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h > nebo \<wchar.h >|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce převodu řetězců na numerické hodnoty](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
