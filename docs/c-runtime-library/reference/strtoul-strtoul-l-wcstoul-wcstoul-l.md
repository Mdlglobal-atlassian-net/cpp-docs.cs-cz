---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 4/2/2020
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
- _o__strtoul_l
- _o__wcstoul_l
- _o_strtoul
- _o_wcstoul
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 60ae432fb11c5a29da2c4830c2a85305c6eaa46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365619"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Převeďte řetězce na neznaménkovou hodnotu dlouhého čísla.

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
Řetězec ukončený hodnotou null pro převod.

*endptr*<br/>
Ukazatel na znak, který zastaví skenování.

*base*<br/>
Číslo základny k použití.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**strtoul** vrátí převedenou hodnotu, pokud existuje, nebo **ULONG_MAX** při přetečení. **strtoul** vrátí hodnotu 0, pokud nelze provést žádný převod. **wcstoul** vrací hodnoty analogicky k **strtoul**. Pro obě funkce je **errno** nastaveno na **ERANGE,** pokud dojde k přetečení nebo podtečení.

Další informace o tomto a dalších návratových kódech naleznete v [_doserrno, errno, _sys_errlist a _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Poznámky

Každá z těchto funkcí převede vstupní řetězec *strSource* na **neznaménkovou** **dlouhou**.

**strtoul** přestane číst řetězec *strSource* na první znak, který nelze rozpoznat jako součást čísla. Může se jedná o ukončující znak null nebo první číselný znak větší nebo roven *základně*. Nastavení **LC_NUMERIC** kategorie národního prostředí určuje rozpoznání znaku radix v *strSource*; Další informace naleznete [v tématu setlocale](setlocale-wsetlocale.md). **strtoul** a **wcstoul** používají aktuální národní prostředí; **_strtoul_l** a **_wcstoul_l** jsou identické s tím rozdílem, že místo toho používají národní prostředí předané. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud *endptr* není **NULL**, ukazatel na znak, který zastavil skenování je uložen v umístění odkazuje *endptr*. Pokud nelze provést žádný převod (nebyly nalezeny žádné platné číslice nebo byl zadán neplatný základ), hodnota *strSource* je uložena v umístění, na které se vztahuje *endptr*.

**wcstoul** je širokoznaková verze **strtoul**; jeho *argument strSource* je řetězec s širokým znakem. V opačném případě se tyto funkce chovají stejně.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul (Strtoul)**|**strtoul (Strtoul)**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**strtoul** očekává *strSource* přejděte na řetězec následujícího formuláře:

> [*mezery*] [{**+** **-**&#124; }] [**0** [{ **x** &#124; **X** }]] [*číslice* &#124; *písmena*]

*Prázdné znaky* se mohou skládat z mezer a znaků tabulátoru, které jsou ignorovány. *číslice* jsou jedna nebo více desetinných míst. *písmena* jsou jedno nebo více písmen "a" přes "z" (nebo "A" až "Z"). První znak, který se nevejde do tohoto formuláře zastaví skenování. Pokud je *základna* mezi 2 a 36, používá se jako základ čísla. Pokud *base* je 0, počáteční znaky řetězce ukázal *strSource* se používají k určení základu. Pokud je první znak 0 a druhý znak není 'x' nebo 'X', řetězec je interpretován jako osmičkové celé číslo. Pokud je první znak '0' a druhý znak je 'x' nebo 'X', řetězec je interpretován jako šestnáctkové celé číslo. Pokud je první znak '1' až '9', řetězec je interpretován jako desítkové celé číslo. Písmenům "a" přes "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; povolena jsou pouze písmena, jejichž přiřazené hodnoty jsou menší než *základní.* První znak mimo rozsah základny zastaví skenování. Pokud je například *základna* 0 a první naskenovaný znak je "0", předpokládá se osmičkové celé číslo a znak "8" nebo "9" zastaví prohledávací číslo. **strtoul** umožňuje plus**+**( )**-** nebo minus ( ) znaménko prefix; znaménko příkonu mínus označuje, že vrácená hodnota je negována.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strtoul (Strtoul)**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h> \<nebo wchar.h>|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h> \<nebo wchar.h>|

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
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
