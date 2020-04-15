---
title: strtoll, _strtoll_l, wcstoll, _wcstoll_l
ms.date: 4/2/2020
api_name:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
- _o__strtoll_l
- _o__wcstoll_l
- _o_strtoll
- _o_wcstoll
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: d5a0ce8cb2c1d5f88d5439b99047609b32c8d2ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365181"
---
# <a name="strtoll-_strtoll_l-wcstoll-_wcstoll_l"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Převede řetězec na **dlouhou** **dlouhou** hodnotu.

## <a name="syntax"></a>Syntaxe

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Řetězec ukončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví prohledávací.

*base*<br/>
Číslo základny k použití.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**strtoll** vrátí hodnotu, která je reprezentována v řetězci *strSource*, s výjimkou případů, kdy by reprezentace způsobila přetečení – v takovém případě vrátí **LLONG_MAX** nebo **LLONG_MIN**. Funkce vrátí hodnotu 0, pokud nelze provést žádný převod. **wcstoll** vrací hodnoty analogicky **strtoll**.

**LLONG_MAX** a **LLONG_MIN** jsou definovány v LIMITECH. H.

Pokud *strSource* je **NULL** nebo *základna* je nenulová a buď menší než 2 nebo větší než 36, **errno** je nastavena na **EINVAL**.

Další informace o návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **strtoll** převede *strSource* na **dlouhou** **.** Obě funkce zastavit čtení řetězce *strSource* na první znak, které nelze rozpoznat jako součást čísla. Může se jedná o ukončující znak null nebo první číselný znak, který je větší nebo roven *základně*. **wcstoll** je širokoznaková verze **strtollu**; jeho *argument strSource* je řetězec s širokým znakem. V opačném případě se tyto funkce chovají stejně.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

Nastavení **kategorie LC_NUMERIC** národního prostředí určuje rozpoznávání znaku radix v *strSource*; Další informace naleznete [v tématu setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkce, které nemají **příponu _l** používají aktuální národní prostředí; **_strtoll_l** a **_wcstoll_l** jsou shodné s odpovídajícími funkcemi, které nemají příponu, s tím rozdílem, že místo toho používají národní prostředí, které je předáno. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování je uložen v umístění, které je odkazuje *na endptr*. Pokud nelze provést žádný převod (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložena v umístění, na které je odkazováno *endptr*.

**strtoll** očekává *strSource* přejděte na řetězec následujícího formuláře:

> [*mezery*] [{**+** **-**&#124; }] [**0** [{ **x** &#124; **X** }]] [*číslice* &#124; *písmena*]

*Prázdné znaky* se mohou skládat z mezer a znaků tabulátoru, které jsou ignorovány; *číslice* jsou jedno nebo více desetinných míst; *písmena* jsou jedno nebo více písmen "a" přes "z" (nebo "A" až "Z"). První znak, který se nevejde do tohoto formuláře zastaví skenování. Pokud je *základna* mezi 2 a 36, používá se jako základ čísla. Pokud *base* je 0, počáteční znaky řetězce, který je odkazován *strSource* se používají k určení základu. Pokud je první znak '0' a druhý znak není 'x' nebo 'X', řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak '0' a druhý znak je 'x' nebo 'X', řetězec je interpretován jako šestnáctkové celé číslo. Pokud je první znak '1' až '9', řetězec je interpretován jako desítkové celé číslo. Písmenům "a" přes "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; povolena jsou pouze písmena, jejichž přiřazené hodnoty jsou menší než *základní.* První znak mimo rozsah základny zastaví skenování. Například pokud *base* je 0 a první znak naskenované je '0', předpokládá se osmičkové celé číslo a znak '8' nebo '9' zastaví skenování.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoll**, **_strtoll_l**|\<stdlib.h>|
|**wcstoll**, **_wcstoll_l**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce řetězec na číselnou hodnotu](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
