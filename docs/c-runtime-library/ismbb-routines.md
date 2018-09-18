---
title: _ismbb – rutiny | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _ismbb
- ismbb
dev_langs:
- C++
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86587495353090ced63d0487991f4275d3d0d5d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092517"
---
# <a name="ismbb-routines"></a>_ismbb – rutiny

Testuje danou celočíselnou hodnotu `c` na určitou podmínku, pomocí aktuálního národního prostředí nebo zadané kategorie stavu převodu LC_CTYPE.

|||
|-|-|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|

## <a name="remarks"></a>Poznámky

Každá rutina v sadě `_ismbb` testuje danou celočíselnou hodnotu `c` na určitou podmínku. Výsledek testu závisí na vícebajtové znakové stránky, který je v platnosti. Standardně je vícebajtová znaková stránka nastavena na ANSI znakovou stránku, která se získá z operačního systému při spuštění programu. Můžete použít [_getmbcp](../c-runtime-library/reference/getmbcp.md) se dotázat na vícebajtové znakové stránce, která se používá, nebo [_setmbcp](../c-runtime-library/reference/setmbcp.md) ho změnit.

Výstupní hodnota je ovlivněna nastavením `LC_CTYPE` kategorie nastavení národního prostředí; Další informace najdete v článku [setlocale _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Verze těchto funkcí, které nemají **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; ty, které mají **_l** přípona jsou identické, s výjimkou, že místo toho se použijte parametr národního prostředí, které je předáno.

Rutiny v `_ismbb` řady testování dané celé číslo `c` následujícím způsobem.

|Rutina|Testovací podmínky bajtu|
|-------------|-------------------------|
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Stejné jako `_ismbbprint`, ale `_ismbbgraph` neobsahuje znak mezery (0x20).|
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Ne-ASCII textový symbol jiný než interpunkce. Například pouze v kódové stránce 932 `_ismbbkalnum` testy pro alfanumerické znaky katakana.|
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 – 0xDF). Specifické pro znakovou stránku 932.|
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Ne-ASCII text nebo ne ASCII interpunkční symbol. Například pouze v kódové stránce 932 `_ismbbkprint` testy pro alfanumerické znaky katakana nebo interpunkční znaky katakana (rozsah: 0xA1 – 0xDF).|
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Ne-ASCII interpunkce. Například pouze v kódové stránce 932 `_ismbbkpunct` interpunkční znaménka katakana.|
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|První bajt vícebajtového znaku. Například v kódové stránce 932 pouze platné rozsahy jsou 0x81 – 0x9F, 0xE0 – 0xFC.|
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** obsahuje znak mezery (0x20).|
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Druhý bajt vícebajtového znaku. Například v kódové stránce 932 pouze platné rozsahy jsou 0x40 – 0x7E, 0x80 – 0xEC.|

Následující tabulka zobrazuje hodnoty ORed, které tvoří testovací podmínky pro tyto rutiny. Konstanty manifestu `_BLANK`, `_DIGIT`, `_LOWER`, `_PUNCT`, a `_UPPER` jsou definovány v souboru Ctype.h.

|Rutina|_BLANK|_DIGIT|NIŽŠÍ|_PUNCT|HORNÍ|Non-<br /><br /> ASCII<br /><br /> text|Non-<br /><br /> ASCII<br /><br /> punct|
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

`_ismbb` Rutiny jsou implementovány jako funkce i makra. Další informace o způsobu volby některé implementace naleznete v tématu [doporučení k výběru mezi funkcemi a makry](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../c-runtime-library/byte-classification.md)<br/>
[is, isw – rutiny](../c-runtime-library/is-isw-routines.md)<br/>
[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)<br/>
[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)