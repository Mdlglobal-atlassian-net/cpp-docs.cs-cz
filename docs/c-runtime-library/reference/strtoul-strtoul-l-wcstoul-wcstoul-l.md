---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 11/04/2016
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: 29edd517b9aa4737497a36557820bf45b6b9804f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946329"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Převede řetězce na celočíselnou hodnotu bez znaménka.

## <a name="syntax"></a>Syntaxe

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**strtoul** vrátí převedenou hodnotu, pokud existuje, nebo **ULONG_MAX** při přetečení. **strtoul** vrátí hodnotu 0, pokud převod nelze provést. **wcstoul** vrací hodnoty obdobně **strtoul**. Pro obě funkce je **errno** nastaveno na **ERANGE** , pokud dojde k přetečení nebo podtečení.

Další informace o tomto a dalších návratových kódech naleznete v tématech [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí převede vstupní řetězec *strSource* na **unsigned** **Long**.

**strtoul** zastaví čtení řetězce *strSource* u prvního znaku, který nelze rozpoznat jako součást čísla. Může to být ukončující znak null nebo se může jednat o první číselný znak, který je větší nebo roven *základní*. Nastavení kategorie **LC_NUMERIC** národního prostředí Určuje rozpoznávání znaku základu v *strSource*; Další informace naleznete v tématu [setlocale](setlocale-wsetlocale.md). **strtoul** a **wcstoul** používají aktuální národní prostředí; **_strtoul_l** a **_wcstoul_l** jsou stejné s tím rozdílem, že místo toho používají předané národní prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *endptr* není **null**, ukazatel na znak, který zastavil skenování, je uložen v umístění, na které odkazuje *endptr*. Pokud převod nelze provést (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložena v umístění, na které odkazuje *endptr*.

**wcstoul** je **strtoul**verze s velkým znakem; jeho argument *strSource* je řetězec s velkým znakem. V opačném případě se tyto funkce chovají identicky.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**strtoul** očekává, že *strSource* odkazuje na řetězec v následujícím tvaru:

> [*prázdné znaky*] [{ **+** &#124; &#124; &#124; }] [0 [{x x}]] [číslice písmen] **-**

*Mezera se může skládat* z mezer a znaků tabulátoru, které jsou ignorovány. *číslice* jsou jednu nebo více desítkových číslic. *písmeny* jsou jedno nebo více písmen "a" až "z" (nebo "a" až "z"). První znak, který se nevejde do tohoto formuláře zastaví kontrolu. Pokud je *základ* mezi 2 a 36, použije se jako základ čísla. Pokud je *základ* 0, pro určení základu se použijí počáteční znaky řetězce, na který odkazuje *strSource* . Pokud je první znak 0 a druhý znak není x nebo X, řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak "0" a druhý znak je "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; povolena jsou pouze písmena, jejichž přiřazené hodnoty jsou menší než *Base* . První znak mimo rozsah základny zastaví skenování. Pokud je například *základ* 0 a první naskenovaný znak je "0", předpokládá se osmičkové celé číslo a znak "8" nebo "9" zastaví kontrolu. **strtoul** umožňuje znaménko plus **+** () nebo mínus **-** () znaménko; úvodní znaménko mínus označuje, že návratová hodnota je negace.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<Stdlib. h > nebo \<WCHAR. h >|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
