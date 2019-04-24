---
title: Funkce řetězců na numerické hodnoty
ms.date: 11/04/2016
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: 3f24b75c2fdb3aa0d84b16874d2d01f1cb96d4b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304550"
---
# <a name="string-to-numeric-value-functions"></a>Funkce řetězců na numerické hodnoty

- [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>Poznámky

Každá funkce **strtod** řady převede řetězec zakončený hodnotou null je číselná hodnota. V následující tabulce jsou uvedeny dostupné funkce.

|Funkce|Popis|
|--------------|-----------------|
|`strtod`|Převod řetězce na hodnotu s plovoucí desetinnou dvojitou přesností|
|`strtol`|Převod řetězce na dlouhé celé číslo|
|`strtoul`|Převod řetězce na dlouhé celé číslo bez znaménka|
|`_strtoi64`|Převod řetězce na 64-bit `__int64` celé číslo|
|`_strtoui64`|Převést řetězec na unsigned 64-bit `__int64` celé číslo|

`wcstod`, `wcstol`, `wcstoul`, a `_wcstoi64` jsou širokoznaké verze `strtod`, `strtol`, `strtoul`, a `_strtoi64`v uvedeném pořadí. Řetězcový argument pro každý z těchto funkcí širokého znaku je řetězec širokého znaku; Každá funkce chová stejně jako jeho protějšek jedním jednobajtového znaku jinak.

`strtod` Funkce přebírá dva argumenty: vstupní řetězec je první a druhý ukazatel na znak, který ukončí proces převodu. `strtol`, `strtoul`, **_strtoi64 –** a **_strtoui64 –** trvat třetí argument jako základna čísla pro použití v procesu převodu.

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako hodnotu zadaného typu. Každá funkce zastaví čtení řetězce u prvního znaku, který nebude rozpoznán jako část čísla. Může to být ukončující znak null. Pro `strtol`, `strtoul`, `_strtoi64`, a `_strtoui64`, tento ukončující znak může být také první číselný znak větší než nebo rovna hodnotě základní uživatelem zadané číslo.

Pokud uživatel uvedl ukazatel na znak koncové převod není nastavená na **NULL** během volání, ukazatel na znak, který zastavil skenování se uloží existuje místo. Pokud žádné převody nemohou být provedeny (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota ukazatele na řetězec je uložen na této adrese.

`strtod` očekává, že řetězec má následující formu:

[*prázdné znaky*] [*přihlašování*] [`digits`] [**.** `digits`] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*přihlašování*] `digits`]

A *prázdné znaky* může skládat ze znaků mezera nebo tabulátor, které jsou ignorovány; *přihlašování* je buď plus (**+**) nebo minus (**-**); a `digits` jsou jeden nebo více desítkových číslic. Pokud se před číselnou soustavou znaků se nezobrazí žádné číslice, alespoň číslice se musí nacházet za číselnou soustavou znaků. Může být následován desítkových číslic exponentu, které se skládají z úvodního písmene (**d**, **D**, **e**, nebo **E**) a volitelně celé číslo se znaménkem. Pokud se nezobrazí část ani Číselná soustava znaků, považován za Číselná soustava znaků postupuje podle poslední číslice v řetězci. První znak, který není vhodná pro tento formulář zastaví skenování.

`strtol`, `strtoul`, `_strtoi64`, A `_strtoui64` funkce očekávat na řetězec v následujícím formátu:

[*whitespace*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [`digits`]

Pokud je základní argument mezi 2 a 36, použije se jako základ pro číslo. Pokud je 0, počáteční znaky odkazuje end převod ukazatele se používají ke stanovení základu. Pokud je první znak 0 a druhý znak není "x" nebo "X", řetězec je interpretován jako osmičkové celé číslo. v opačném případě je interpretován jako desítkové číslo. Pokud je první znak "0" a druhý znak je písmeno "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; jenom písmena, jejichž přiřazené hodnoty jsou menší než *základní* nejsou povoleny. `strtoul` a `_strtoui64` povolit plus (**+**) nebo minus (**-**) přihlašování předponu; úvodní mínus znamená, že návratová hodnota je negovat.

Výstupní hodnota je ovlivněna nastavením `LC_NUMERIC` nastavením kategorie národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v.

Při hodnotě vrácené tyto funkce by způsobilo přetečení nebo podtečení, nebo pokud převod není možný, speciální případových hodnoty jsou vráceny, jak je znázorněno:

|Funkce|Podmínka|Hodnota vrácená|
|--------------|---------------|--------------------|
|`strtod`|přetečení|+/- `HUGE_VAL`|
|`strtod`|Podtečení nebo žádný převod|0|
|`strtol`|+ Přetečení|**LONG_MAX**|
|`strtol`|-Přetečení|**LONG_MIN**|
|`strtol`|Podtečení nebo žádný převod|0|
|`_strtoi64`|+ Přetečení|**_I64_MAX**|
|`_strtoi64`|-Přetečení|**_I64_MIN**|
|`_strtoi64`|Žádný převod|0|
|`_strtoui64`|přetečení|**_UI64_MAX**|
|`_strtoui64`|Žádný převod|0|

**_I64_MAX**, _**I64_MIN**, a **_UI64_MAX** jsou definovány v omezení. H.

`wcstod`, `wcstol`, `wcstoul`, `_wcstoi64`, a `_wcstoui64` jsou širokoznaké verze `strtod`, `strtol`, `strtoul`, `_strtoi64`, a `_strtoui64`v uvedeném pořadí; ukazatel na end sady konverzi argument pro každý z těchto funkcí širokého znaku je širokoznaký řetězec. Jinak každá z těchto funkcí širokého znaku chová stejně jako jeho protějšek jedním jednobajtového znaku.

## <a name="see-also"></a>Viz také:

[Převod dat](../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Podpora plovoucí desetinné čárky](../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
