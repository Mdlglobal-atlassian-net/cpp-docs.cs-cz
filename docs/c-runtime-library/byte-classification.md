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
ms.openlocfilehash: 9c00d0c0165bdae15ba5fc413d00a99bf4601b21
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632398"
---
# <a name="byte-classification"></a>Klasifikace bajtů

Každá z těchto rutin testuje zadaný bajt vícebajtového znaku pro splnění podmínky. S výjimkou toho, kde je určeno jinak, výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v.

> [!NOTE]
> Podle definice jsou znaky ASCII mezi 0 a 127 podmnožinou všech vícebajtových znakových sad. Například znakové sady Japonská katakana zahrnuje ASCII, jakož i jiné znaky než ASCII.

Předdefinované konstanty v následující tabulce jsou definovány v \<ctype.h >.

## <a name="multibyte-character-byte-classification-routines"></a>Rutiny klasifikace bajtů vícebajtových znaků

|Rutina|Testovací podmínky bajtu|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Vedoucí bajt; výsledek testu závisí na **LC_CTYPE** nastavením kategorie aktuálního národního prostředí|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum** &#124; &#124; **_ismbbkalnum –**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha** &#124; &#124; **_ismbbkalnum –**|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Stejné jako **_ismbbprint –**, ale **_ismbbgraph –** neobsahuje znak mezery (0x20)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Ne-ASCII textový symbol jiný než interpunkce. Například pouze v kódové stránce 932 **_ismbbkalnum –** testy pro alfanumerické znaky katakana|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 – 0xDF), pouze znaková stránky 932|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Ne-ASCII text nebo ne ASCII interpunkční symbol. Například pouze v kódové stránce 932 **_ismbbkprint –** testy pro alfanumerické znaky katakana nebo interpunkční znaky katakana (rozsah: 0xA1 – 0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Ne-ASCII interpunkce. Například pouze v kódové stránce 932 **_ismbbkpunct –** interpunkční znaménka katakana.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|První bajt vícebajtového znaku. Například v kódové stránce 932 pouze platné rozsahy jsou 0x81 – 0x9F, 0xE0 – 0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint** &#124; &#124; **_ismbbkprint –**. **ismbbprint** obsahuje znak mezery (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct** &#124; &#124; **_ismbbkpunct –**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Druhý bajt vícebajtového znaku. Například v kódové stránce 932 pouze platné rozsahy jsou 0x40 – 0x7E, 0x80 – 0xEC.|
|[_ismbslead – _ismbslead_l –](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Vedoucí bajt (v kontextu řetězec)|
|[ismbstrail – _ismbstrail_l –](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Druhý bajt (v kontextu řetězec)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Byte návratový typ podle předchozí bajtů|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Vrátí typ bajtu v rámci řetězce|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Sleduje stav převodu vícebajtových znaků.|

**MB_LEN_MAX** makro definované v \<limits.h >, rozšíří na maximální délku v bajtech, která může mít libovolného vícebajtového znaku. **MB_CUR_MAX**definované v \<stdlib.h >, rozšíří na maximální délku v bajtech libovolného vícebajtového znaku v aktuálním národním prostředí.

## <a name="see-also"></a>Viz také:

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)