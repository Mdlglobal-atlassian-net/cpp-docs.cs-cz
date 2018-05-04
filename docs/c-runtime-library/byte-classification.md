---
title: Klasifikace bajtů | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.types.bytes
dev_langs:
- C++
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f1051ea7b8d4cc3a3f38a5a95f015674ac3e35c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="byte-classification"></a>Klasifikace bajtů

Každý z těchto rutin testy zadané bajtové vícebajtových znaků pro spokojenost podmínku. S výjimkou toho, kde je to uvedeno jinak, výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná.

> [!NOTE]
> Podle definice, jsou podmnožinou všech vícebajtových znakových sad znaky ASCII rozsahu od 0 do 127. Například obsahuje japonské katakana znaková sada ASCII, jakož i jiné znaky než ASCII.

Předdefinované konstanty v následující tabulce jsou definovány v \<ctype.h >.

## <a name="multibyte-character-byte-classification-routines"></a>Rutiny klasifikace bajtů vícebajtových znaků

|Rutina|Stav testu bajtů|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Vést bajtů; výsledek testu závisí na **LC_CTYPE –** kategorie nastavení aktuální národní prostředí|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum –** &#124; &#124; **_ismbbkalnum –**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha –** &#124; &#124; **_ismbbkalnum –**|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Stejné jako **_ismbbprint –**, ale **_ismbbgraph –** neobsahuje znak mezery (0x20)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Symbol text ASCII jiného typu než interpunkce. Například v pouze znaková stránka 932 **_ismbbkalnum –** testů pro katakana alfanumerické|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF), pouze znaková stránka 932|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Jiné než ASCII text nebo jiné sady než ASCII interpunkční symbol. Například v pouze znaková stránka 932 **_ismbbkprint –** testů pro katakana alfanumerické nebo katakana interpunkce (rozsah: 0xA1 - 0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Interpunkce non-ASCII. Například v pouze znaková stránka 932 **_ismbbkpunct –** testů pro katakana interpunkce.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|První bajt vícebajtových znaků. Například v kódu stránky 932 pouze, platné rozsahy jsou 0x81 - 0x9F, 0xE0 - 0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint –** &#124; &#124; **_ismbbkprint –**. **ismbbprint –** obsahuje znak mezery (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct –** &#124; &#124; **_ismbbkpunct –**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Druhý bajt vícebajtových znaků. Například v kódu stránky 932 pouze, platné rozsahy jsou 0x40 - 0x7E, 0x80 - 0xEC.|
|[_ismbslead –, _ismbslead_l –](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Vést bajtů (v kontextu řetězec)|
|[ismbstrail –, _ismbstrail_l –](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Bajt (v kontextu řetězec)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Typ návratové bajtů podle předchozích bajtů|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Návratový typ bajtů v rámci řetězce|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Sleduje stav převodu vícebajtových znaků.|

**Mb_len_max –** makro, definované v \<Limits.h – >, rozšíří na maximální délku v bajtech, které může mít žádné vícebajtových znaků. **Mb_cur_max –**, definované v \<stdlib.h >, rozšíří na maximální délku v bajtech žádné vícebajtových znaků v aktuální národní prostředí.

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)