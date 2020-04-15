---
title: strtoull, _strtoull_l, wcstoull, _wcstoull_l
ms.date: 4/2/2020
api_name:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
- _o__strtoull_l
- _o__wcstoull_l
- _o_strtoull
- _o_wcstoull
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
ms.openlocfilehash: 5a27218b9d83314f995df30fbe21d97031d371af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354053"
---
# <a name="strtoull-_strtoull_l-wcstoull-_wcstoull_l"></a>strtoull, _strtoull_l, wcstoull, _wcstoull_l

Převede řetězce na nepodepsanou dlouhou hodnotu dlouhého čísla.

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
Řetězec ukončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví prohledávací.

*base*<br/>
Číslo základny k použití.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**strtoull** vrátí převedenou hodnotu, pokud existuje, nebo **ULLONG_MAX** na přetečení. **strtoull** vrátí 0, pokud nelze provést žádný převod. **wcstoull** vrací hodnoty analogicky **k strtoull**. Pro obě funkce je **errno** nastaveno na **ERANGE,** pokud dojde k přetečení nebo podtečení.

Další informace o návratových kódech naleznete [v tématech errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí převede vstupní řetězec *strSource* na **nepodepsanou** **dlouhou** **řaduinnou** hodnotu.

**strtoull** přestane číst řetězec *strSource* na první znak, který nelze rozpoznat jako součást čísla. Může se jedná o ukončující znak null nebo první číselný znak, který je větší nebo roven *základně*. Nastavení **LC_NUMERIC** kategorie národního prostředí určuje rozpoznání znaku radix v *strSource*; Další informace naleznete [v tématu setlocale, _wsetlocale](setlocale-wsetlocale.md). **strtoull** a **wcstoull** používají aktuální národní prostředí; **_strtoull_l** a **_wcstoull_l** místo toho použít národní prostředí, které je předáno, ale jsou identické jinak. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování je uložen v umístění, které je odkazuje *na endptr*. Pokud nelze provést žádný převod (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota *strSource* je uložena v umístění, na které je odkazováno *endptr*.

**wcstoull** je širokoznaková verze **strtoullu** a jeho argument *strSource* je řetězec s širokým znakem. V opačném případě se tyto funkce chovají stejně.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull (Strtoull)**|**strtoull (Strtoull)**|**wcstoull řekl:**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull** očekává *strSource* přejděte na řetězec následujícího formuláře:

> [*mezery*] [{**+** **-**&#124; }] [**0** [{ **x** &#124; **X** }]] [*číslice* &#124; *písmena*]

*Prázdné znaky* se mohou skládat z mezer a znaků tabulátoru, které jsou ignorovány. *číslice* jsou jedna nebo více desetinných míst. *písmena* jsou jedno nebo více písmen "a" přes "z" (nebo "A" až "Z"). První znak, který se nevejde do tohoto formuláře zastaví skenování. Pokud je *základna* mezi 2 a 36, používá se jako základ čísla. Pokud *base* je 0, počáteční znaky řetězce, který je odkazován *strSource* se používají k určení základu. Pokud je první znak '0' a druhý znak není 'x' nebo 'X', řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak '0' a druhý znak je 'x' nebo 'X', řetězec je interpretován jako šestnáctkové celé číslo. Pokud je první znak '1' až '9', řetězec je interpretován jako desítkové celé číslo. Písmenům "a" přes "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; povolena jsou pouze písmena, jejichž přiřazené hodnoty jsou menší než *základní.* První znak mimo rozsah základny zastaví skenování. Například pokud *base* je 0 a první znak naskenované je '0', předpokládá se osmičkové celé číslo a znak '8' nebo '9' zastaví skenování. **strtoull** umožňuje znaménko plus (**+**) nebo mínus (**-**) předponu; znaménko příkonu mínus označuje, že vrácená hodnota je negována.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoull (Strtoull)**|\<stdlib.h>|
|**wcstoull řekl:**|\<stdlib.h> \<nebo wchar.h>|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funkce řetězec na číselnou hodnotu](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
