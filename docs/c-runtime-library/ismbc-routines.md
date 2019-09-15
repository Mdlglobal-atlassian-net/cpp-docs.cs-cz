---
title: _ismbc – rutiny
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 6dc14f269cafa8ccc343c5403ab0e23d319c71c3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940170"
---
# <a name="_ismbc-routines"></a>_ismbc – rutiny

Každá rutina **_ismbc** testuje daný vícebajtový `c` znak pro určitou podmínku.

|||
|-|-|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>Poznámky

Výsledek testu každé rutiny **_ismbc** závisí na vícebajtové znakové stránce. Vícebajtové kódové stránky mají jednobajtové abecední znaky. Ve výchozím nastavení je Vícebajtová znaková stránka nastavena na standardní znakovou stránku ANSI získanou z operačního systému při spuštění programu. Můžete zadat dotaz nebo změnit vícebajtovou znakovou stránku, která se používá s [_getmbcp](../c-runtime-library/reference/getmbcp.md) nebo [_setmbcp](../c-runtime-library/reference/setmbcp.md), v uvedeném pořadí.

Výstupní hodnota je ovlivněna `LC_CTYPE` nastavením kategorie národního prostředí; další informace naleznete v tématu [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) . Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s příponou **_l** jsou stejné s tím rozdílem, že místo toho používají předaný parametr národního prostředí.

|Rutina|Testovací podmínka|Příklad znakové stránky 932|
|-------------|--------------------|---------------------------|
|[_ismbcalnum, _ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Písmena|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění anglického písmene ASCII: Viz příklady pro `_ismbcdigit` a `_ismbcalpha`.|
|[_ismbcalpha, _ismbcalpha_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Abecedy|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění anglického písmene ASCII: Podívejte se na `_ismbcupper` příklady `_ismbclower`pro a; nebo na písmeno Katakana: 0xA6<=`c`<=0xDF.|
|[_ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Základní|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění číslice ASCII: 0x30 < =`c`< = 0x39.|
|[_ismbcgraph, _ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Graphic|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění libovolného tisknutelného znaku ASCII nebo katakana s výjimkou mezer (). Viz příklady pro `_ismbcdigit`, `_ismbcalpha`a `_ismbcpunct`.|
|[_ismbclegal, _ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Platný vícebajtový znak|Vrátí nenulovou hodnotu, pokud je první bajt `c` v rozsahu 0x81-0x9F nebo 0xE0-0xFC, zatímco druhý bajt je v rozsahu 0x40-0x7E nebo 0x80-FC.|
|[_ismbclower, _ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Malá písmena|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění písmena anglické abecedy ASCII: 0x61 < =`c`< = 0x7A.|
|[_ismbcprint, _ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Tisknutelný|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění libovolného tisknutelného znaku ASCII nebo katakana, včetně mezer (): Viz příklady pro `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha`a. `_ismbcpunct`|
|[_ismbcpunct, _ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Interpunkční znaménka|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění libovolného interpunkční znaku ASCII nebo Katakana.|
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Mezera nebo horizontální tabulátor|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění znaku mezery nebo znak horizontálního tabulátoru: `c`= 0x20 nebo `c`= 0x09.|
|[_ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Typy|Vrátí nenulovou hodnotu pouze v případě `c` , že je prázdný znak: `c`= 0x20 nebo 0x09 < =`c`< = 0x0D.|
|[_ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Vícebajtový symbol|Vrátí nenulovou hodnotu pouze v případě, že 0x8141`c`< = < = 0x81AC.|
|[_ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Velká písmena abecedy|Vrátí nenulovou hodnotu pouze v případě `c` , že je jednobajtové znázornění písmena anglické abecedy ASCII: 0x41 < =`c`< = 0x5A.|

**Konkrétní znaková stránka 932**

Následující rutiny jsou specifické pro znakovou stránku 932.

|Rutina|Testovací podmínka (pouze znaková stránka 932)|
|-------------|-------------------------------------------|
|[_ismbchira, _ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Dvoubajtové znaky Hiragana: 0x829F < =`c`< = 0x82F1.|
|[_ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Dvoubajtové Katakana: 0x8340 < =`c`< = 0x8396.|
|[_ismbcl0, _ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS bez kanji: 0x8140<=`c`<=0x889E.|
|[_ismbcl1, _ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS úroveň-1: 0x889F < =`c`< = 0x9872.|
|[_ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS úroveň 2: 0x989F < =`c`< = 0xEA9E.|

`_ismbcl0`, `_ismbcl1` `c` `c` a `_ismbcl2` zkontrolujte, zda zadaná hodnota odpovídá zkušebním podmínkám popsaným v předchozí tabulce, ale nekontrolují, zda je platný vícebajtový znak. Pokud je nižší bajt v oblastech 0x00-0x3F, 0x7F nebo 0xFD-0xFF, tyto funkce vrátí nenulovou hodnotu, což značí, že znak splňuje podmínku testu. Použijte [_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) k otestování, zda je vícebajtový znak definován.

**KONEC konkrétní kódové stránky 932**

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../c-runtime-library/character-classification.md)<br/>
[is, isw – rutiny](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb – rutiny](../c-runtime-library/ismbb-routines.md)
