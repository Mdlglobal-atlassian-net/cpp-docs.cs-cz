---
title: Funkce řetězců na numerické hodnoty
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: b9d8218bd5a3151e17b7ac380bb86c85dac3e6a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944727"
---
# <a name="string-to-numeric-value-functions"></a>Funkce řetězců na numerické hodnoty

- [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>Poznámky

Každá funkce v rodině **strtod** převede řetězec zakončený hodnotou null na číselnou hodnotu. Dostupné funkce jsou uvedené v následující tabulce.

|Funkce|Popis|
|--------------|-----------------|
|`strtod`|Převést řetězec na hodnotu s dvojitou přesností s plovoucí desetinnou čárkou|
|`strtol`|Převést řetězec na dlouhé celé číslo|
|`strtoul`|Převést řetězec na dlouhé celé číslo bez znaménka|
|`_strtoi64`|Převést řetězec na 64-bitové `__int64` celé číslo|
|`_strtoui64`|Převést řetězec na celé číslo bez znaménka 64-bit `__int64`|

`wcstod`, `wcstol`, `wcstoul`a `strtol` jsouverze`strtod`s libovolným znakem, `_strtoi64`, a v uvedeném pořadí. `strtoul` `_wcstoi64` Řetězcový argument pro každou z těchto funkcí s velkým znakem je řetězec s velkým znakem; Každá funkce se chová stejně jako jeho protějšek s jedním bajtem, jinak.

`strtod` Funkce přebírá dva argumenty: první je vstupní řetězec a druhý ukazatel na znak, který ukončí proces převodu. `strtol`, `strtoul`, **_strtoi64** a **_strtoui64** přebírají třetí argument jako základní číslo pro použití v procesu převodu.

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako číselnou hodnotu zadaného typu. Každá funkce zastaví čtení řetězce u prvního znaku, který není rozpoznán jako část čísla. Může to být ukončující znak null. Pro `strtol`, `strtoul`, a`_strtoi64`je tento ukončovací znak také první číselný znak, který je větší než nebo roven základu číselného zadaného uživatele. `_strtoui64`

Pokud uživatelem zadaný ukazatel na znak konce převodu není v době volání nastaven na **hodnotu null** , místo toho se uloží ukazatel na znak, který zastaví kontrolu. Pokud převod nelze provést (nebyly nalezeny žádné platné číslice nebo byla zadána neplatná základna), hodnota ukazatele řetězce je uložena na adrese.

`strtod`očekává řetězec v následujícím tvaru:

[*prázdné znaky*] [*Sign*] [`digits`] [ **.** `digits` &#124; &#124; &#124; ] [{d d e e} [*Sign]]* `digits`

*Mezera* se může skládat z mezer nebo znaků tabulátoru, které se ignorují. *znaménko* je buď znaménko plus ( **+** ), nebo mínus ( **-** ); a `digits` je jedna nebo více desítkových číslic. Pokud se před znakem základu neobjeví žádné číslice, musí se alespoň jedna objevit za znakem základu. V desítkových číslicích může následovat exponent, který se skládá z úvodního písmene (**d**, **d**, **e**nebo **e**) a volitelně podepsaného celého čísla. Pokud se nezobrazí část exponentu ani číselný znak, předpokládá se, že za poslední číslicí v řetězci bude následovat znak základu. První znak, který se nevejde do tohoto formuláře zastaví kontrolu.

Funkce `strtol`, `strtoul`, `_strtoi64`a očekávajířetězecvnásledujícímtvaru:`_strtoui64`

[*prázdné znaky*] [{ **+** &#124; `digits` &#124; }] [0 [{x x}]] [] **-**

Pokud je základní argument mezi 2 a 36, pak se používá jako základ čísla. Pokud je 0, prvotní znaky, na které se odkazuje ukazatel na konci převodu, se používají k určení základu. Pokud je první znak 0 a druhý znak není x nebo X, řetězec je interpretován jako osmičkové celé číslo; v opačném případě je interpretován jako desítkové číslo. Pokud je první znak "0" a druhý znak je "x" nebo "X", řetězec je interpretován jako hexadecimální celé číslo. Pokud je první znak "1" až "9", řetězec je interpretován jako desítkové celé číslo. Písmenům "a" až "z" (nebo "A" až "Z") jsou přiřazeny hodnoty 10 až 35; povolena jsou pouze písmena, jejichž přiřazené hodnoty jsou menší než *Base* . `strtoul`a `_strtoui64` umožňují znaménko plus **+** () nebo mínus **-** () znaménko; úvodní znaménko mínus označuje, že návratová hodnota je negace.

Výstupní hodnota je ovlivněna nastavením `LC_NUMERIC` kategorie národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) pro další informace. Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají předaný parametr národního prostředí.

Když hodnota vrácená těmito funkcemi by způsobila přetečení nebo podtečení nebo když převod není možný, vrátí se speciální hodnoty Case, jak je uvedeno níže:

|Funkce|Podmínka|Vrácená hodnota|
|--------------|---------------|--------------------|
|`strtod`|Plně|+/- `HUGE_VAL`|
|`strtod`|Podtečení nebo bez převodu|0|
|`strtol`|+ Přetečení|**LONG_MAX**|
|`strtol`|– Přetečení|**LONG_MIN**|
|`strtol`|Podtečení nebo bez převodu|0|
|`_strtoi64`|+ Přetečení|**_I64_MAX**|
|`_strtoi64`|– Přetečení|**_I64_MIN**|
|`_strtoi64`|Bez převodu|0|
|`_strtoui64`|Plně|**_UI64_MAX**|
|`_strtoui64`|Bez převodu|0|

**_I64_MAX**, _**I64_MIN**a **_UI64_MAX** jsou definovány v omezeních. Y.

`wcstod`, `wcstol` `strtol` `strtoul`, `wcstoul` ,a`strtod` jsouverze`_strtoi64`s libovolným znakem,,, a ,vtomtopořadí,ukazatelna`_strtoui64` `_wcstoui64` `_wcstoi64` Argument konec převodu na každou z těchto funkcí s velkým znakem je řetězec s velkým počtem znaků. V opačném případě se každá z těchto funkcí s velkým znakem chová stejně jako protějšek s jedním bytem znaku.

## <a name="see-also"></a>Viz také:

[Převod dat](../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Podpora plovoucí desetinné čárky](../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
