---
title: Klasifikace bajtů
ms.date: 04/04/2018
f1_keywords:
- c.types.bytes
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
ms.openlocfilehash: 7272170bd3a1e765e728451afc245947111ee947
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171564"
---
# <a name="byte-classification"></a>Klasifikace bajtů

Každá z těchto rutin testuje zadaný bajt vícebajtového znaku pro splnění podmínky. S výjimkou případů, kdy je uvedeno jinak, výstupní hodnota je ovlivněna nastavením **LC_CTYPE** kategorie národního prostředí; Další informace naleznete v tématu [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí.

> [!NOTE]
> Podle definice jsou znaky ASCII mezi 0 a 127 podmnožinou všech vícebajtových znakových sad. Například japonská znaková sada Katakana zahrnuje ASCII i jiné znaky než ASCII.

Předdefinované konstanty v následující tabulce jsou definovány v \<CType. h >.

## <a name="multibyte-character-byte-classification-routines"></a>Rutiny klasifikace vícebajtových znakových bajtů

|Rutina|Podmínka testu bajtů|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Vedoucí bajt; výsledek testu závisí na nastavení kategorie **LC_CTYPE** aktuálního národního prostředí.|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum** &#124; isalnum &#124; **_ismbbkalnum**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha** &#124; &#124; **_ismbbkalnum** -alfa|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Stejné jako **_ismbbprint**, ale **_ismbbgraph** nezahrnuje znak mezery (0x20).|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Jiný textový symbol než ASCII jiný než interpunkční znaménko. Například pouze v kódové stránce 932 **_ismbbkalnum** testy pro znaky Katakana.|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1-0xDF), pouze znaková stránka 932|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Text jiný než ASCII nebo symbol interpunkce mimo ASCII. Například pouze v kódové stránce 932 **_ismbbkprint** testy pro znaky Katakana nebo interpunkční znaménka Katakana (rozsah: 0XA1-0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Interpunkční znaménka jiné než ASCII. Například pouze v kódové stránce 932 **_ismbbkpunct** testy pro interpunkční znaménka Katakana.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|První bajt vícebajtového znaku. Například v kódové stránce 932 jsou platné rozsahy 0x81-0x9F, 0xE0-0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint** &#124; &#124; **_ismbbkprint**tisku. **ismbbprint** obsahuje znak mezery (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct** &#124; ispunct &#124; **_ismbbkpunct**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Druhý bajt vícebajtového znaku. Například v kódové stránce 932 jsou platné rozsahy 0x40-0x7E, 0x80-0xEC.|
|[_ismbslead _ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Vedoucí bajt (v kontextu řetězce)|
|[ismbstrail, _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Koncový bajt (v kontextu řetězce)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Typ vrácené bajtů na základě předchozího bajtu|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Návratový typ bajtu v řetězci|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Sleduje stav převodu vícebajtových znaků.|

Makro **MB_LEN_MAX** definované v \<Limits. h > rozšiřuje na maximální délku v bajtech, kterou může mít libovolný vícebajtový znak. **MB_CUR_MAX**definovaná v \<Stdlib. h > rozbalí na maximální délku v bajtech pro libovolný vícebajtový znak v aktuálním národním prostředí.

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)
