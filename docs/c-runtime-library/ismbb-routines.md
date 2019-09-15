---
title: _ismbb – rutiny
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbb
- ismbb
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
ms.openlocfilehash: 374c78ca222f9c63f6b37f26d4cf3a00f48f845e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944533"
---
# <a name="_ismbb-routines"></a>_ismbb – rutiny

Testuje zadanou celočíselnou hodnotu `c` pro konkrétní podmínku pomocí aktuálního národního prostředí nebo zadané kategorie stavu konverze LC_CTYPE.

|||
|-|-|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|

## <a name="remarks"></a>Poznámky

Každá rutina v `_ismbb` rodině testuje danou celočíselnou hodnotu `c` pro konkrétní podmínku. Výsledek testu závisí na vícebajtové znakové stránce, která je v platnosti. Ve výchozím nastavení je Vícebajtová znaková stránka nastavena na znakovou stránku ANSI, která se získá z operačního systému při spuštění programu. [_Getmbcp](../c-runtime-library/reference/getmbcp.md) můžete použít k dotazování na vícebajtovou znakovou stránku, která se používá, nebo [_setmbcp](../c-runtime-library/reference/setmbcp.md) ji změnit.

Výstupní hodnota je ovlivněna nastavením `LC_CTYPE` kategorie národního prostředí; další informace naleznete v tématu [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Verze těchto funkcí, které nemají příponu **_l** , používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají parametr národního prostředí, který je předán.

Rutiny v `_ismbb` rodině testují dané celé číslo `c` následujícím způsobem.

|Rutina|Podmínka testu bajtů|
|-------------|-------------------------|
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Stejné jako `_ismbbprint`, ale `_ismbbgraph` nezahrnuje znak mezery (0x20).|
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Jiný textový symbol než ASCII jiný než interpunkční znaménko. Například pouze `_ismbbkalnum` v kódové stránce 932 testy pro znaky Katakana.|
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1-0xDF). Specifické pro znakovou stránku 932.|
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Text jiný než ASCII nebo symbol interpunkce mimo ASCII. Například pouze `_ismbbkprint` v kódové stránce 932 testy pro znaky Katakana a interpunkční znaménka Katakana (rozsah: 0xA1-0xDF).|
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Interpunkční znaménka jiné než ASCII. Například pouze `_ismbbkpunct` v kódové stránce 932 testy pro interpunkci Katakana.|
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|První bajt vícebajtového znaku. Například v kódové stránce 932 jsou platné rozsahy 0x81-0x9F, 0xE0-0xFC.|
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** obsahuje znak mezery (0x20).|
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Druhý bajt vícebajtového znaku. Například v kódové stránce 932 jsou platné rozsahy 0x40-0x7E, 0x80-0xEC.|

V následující tabulce jsou uvedeny hodnoty ORed, které tvoří testovací podmínky pro tyto rutiny. Konstanty `_BLANK`manifestu `_DIGIT` ,`_PUNCT`,, a`_UPPER` jsou definovány v CType. h. `_LOWER`

|Rutina|_BLANK|_DIGIT|MALÝM|_PUNCT|UMÍSTIT|Bez<br /><br /> ASCII<br /><br /> text|Bez<br /><br /> ASCII<br /><br /> punct|
|-------------|-------------|-------------|-----------|-------------|-----------|------------------------------|-------------------------------|
|`_ismbbalnum`|—|x|x|—|x|x|—|
|`_ismbbalpha`|—|—|x|—|x|x|—|
|`_ismbbblank`|x|—|—|—|—|—|—|
|`_ismbbgraph`|—|x|x|x|x|x|x|
|`_ismbbkalnum`|—|—|—|—|—|x|—|
|`_ismbbkprint`|—|—|—|—|—|x|x|
|`_ismbbkpunct`|—|—|—|—|—|—|x|
|`_ismbbprint`|x|x|x|x|x|x|x|
|`_ismbbpunct`|—|—|—|x|—|—|x|

`_ismbb` Rutiny jsou implementovány jako funkce i jako makra. Další informace o tom, jak zvolit jednu implementaci, najdete v tématu [doporučení pro výběr mezi funkcemi a makry](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../c-runtime-library/byte-classification.md)<br/>
[is, isw – rutiny](../c-runtime-library/is-isw-routines.md)<br/>
[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)<br/>
[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)
