---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
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
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: dbeaf04d34aa20e15de48e99082ed07edb6129ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320479"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Převeďte řetězce na **dlouhou** hodnotu celého čísla.

## <a name="syntax"></a>Syntaxe

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Řetězec*\
Řetězec ukončený hodnotou null pro převod.

*end_ptr*\
Výstupní parametr, nastavený na odkaz na znak za posledním interpretovaným znakem. Ignorováno, pokud **null**.

*Základní*\
Číslo základny k použití.

*Národní prostředí*\
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**strtol**, **wcstol**, **_strtol_l**a **_wcstol_l** vrátí hodnotu reprezentovanou v *řetězci*. Vrátí 0, pokud není možný převod. Pokud by reprezentace způsobila přetečení, vrátí **LONG_MAX** nebo **LONG_MIN**.

**errno** je nastavena na **ERANGE,** pokud dojde k přetečení nebo podtečení. Je nastavena na **EINVAL,** pokud *je řetězec* **NULL**. Nebo pokud *je základna* nenulová a menší než 2 nebo větší než 36. Další informace o **eRANGE**, **EINVAL**a další návratové kódy naleznete [v _doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **strtol**, **wcstol**, **_strtol_l**a **_wcstol_l** převádějí *řetězec* na **dlouhý**. Přestanou číst *řetězec* na první znak není rozpoznán jako součást čísla. Může se jedná o znak ukončující-null nebo první alfanumerický znak větší než nebo rovno *báze*.

**wcstol** a **_wcstol_l** jsou širokoznakové verze **strtol** a **_strtol_l**. Jejich *argument řetězce* je řetězec s širokým znakem. Tyto funkce se chovají stejně jako **strtol** a **_strtol_l** jinak. Nastavení **kategorie LC_NUMERIC** národního prostředí určuje rozpoznání znaku radix (zlomková značka nebo desetinná čárka) v *řetězci*. Funkce **strtol** a **wcstol** používají aktuální národní prostředí. **_strtol_l** a **_wcstol_l** místo toho používají národní prostředí. Další informace naleznete v tématech [setlocale] a [Locale](../../c-runtime-library/locale.md).

Pokud *je end_ptr* **null**, je ignorována. V opačném případě je v umístění, na které odkazuje *end_ptr*, uložen ukazatel na znak, který zastavil skenování. Převod není možný, pokud nejsou nalezeny žádné platné číslice nebo je zadána neplatná základna. Hodnota *řetězce* je pak uložena v umístění, na které se *vztahuje end_ptr*.

**strtol** *očekává,* že řetězec přejde na řetězec následujícího formuláře:

> [*mezery*] [{**+** **-**&#124; }] [**0** [{ **x** &#124; **X** }]] [*alfanumerické ]*

Čtvercové závorky (`[ ]`) obklopují volitelné prvky. Složené závorky a`{ | }`svislé bary ( ) prostorové alternativy pro jeden prvek. *prázdné znaky* se mohou skládat z mezer a znaků tabulátoru, které jsou ignorovány. *alfanumerické jsou* desetinné číslice nebo písmena "a" až "z" (nebo "A" až "Z"). První znak, který se nevejde do tohoto formuláře, zastaví skenování. Pokud je *základna* mezi 2 a 36, použije se jako základ čísla. Pokud *je základna* 0, počáteční znaky řetězce, na který se odkazuje *řetězec,* se používají k určení základu. Pokud je první znak 0 a druhý znak není 'x' nebo 'X', řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak '0' a druhý znak je 'x' nebo 'X', řetězec je interpretován jako šestnáctkové celé číslo. Pokud je první znak '1' až '9', řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35. Skenování umožňuje pouze písmena, jejichž hodnoty jsou menší než *základní*. První znak mimo rozsah základny zastaví skenování. Předpokládejme například, že *řetězec* začíná řetězcem "01". Pokud je *základna* 0, skener předpokládá, že se jedná o osmičkové celé číslo. Znak "8" nebo "9" zastaví skenování.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> \<nebo wchar.h>|
|**_strtol_l**|\<stdlib.h>|
|**_wcstol_l**|\<stdlib.h> \<nebo wchar.h>|

Funkce **_strtol_l** **_wcstol_l** a jsou specifické pro společnost Microsoft, nikoli součástí knihovny Standard C. Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../compatibility.md).

## <a name="example"></a>Příklad

Viz příklad [strtod](strtod-strtod-l-wcstod-wcstod-l.md)pro .

## <a name="see-also"></a>Viz také

[Převod dat](../data-conversion.md)\
[Národní prostředí](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Funkce řetězec na číselnou hodnotu](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
