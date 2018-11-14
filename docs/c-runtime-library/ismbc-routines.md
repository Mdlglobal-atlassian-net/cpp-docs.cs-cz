---
title: _ismbc – rutiny
ms.date: 11/04/2016
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 97094c6773ee6b67655dacc557335ed222fed311
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326729"
---
# <a name="ismbc-routines"></a>_ismbc – rutiny

Každý **_ismbc** rutina testujte daný vícebajtový znak `c` na určitou podmínku.

|||
|-|-|
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>Poznámky

Výsledek testu každé **_ismbc** rutina závisí na vícebajtové znakové stránky v platnosti. Vícebajtové znakové stránky obsahují jednobajtové abecední znaky. Standardně je vícebajtová znaková stránka nastavena na systém výchozí znakovou stránku ANSI získanou z operačního systému při spuštění programu. Můžete zadat dotaz nebo změnit vícebajtovou znakovou stránku pomocí [_getmbcp](../c-runtime-library/reference/getmbcp.md) nebo [_setmbcp](../c-runtime-library/reference/setmbcp.md)v uvedeném pořadí.

Výstupní hodnota je ovlivněna `LC_CTYPE` nastavením kategorie národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v.

|Rutina|Testovací podmínka|Příklad znakové stránky 932|
|-------------|--------------------|---------------------------|
|[_ismbcalnum – _ismbcalnum_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumerické znaky|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění písmena anglické abecedy ASCII: viz příklady pro `_ismbcdigit` a `_ismbcalpha`.|
|[_ismbcalpha – _ismbcalpha_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Abecedy|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění písmena anglické abecedy ASCII: viz příklady pro `_ismbcupper` a `_ismbclower`; nebo písma katakana písmeno: 0xA6 < =`c`< = 0xDF.|
|[_ismbcdigit – _ismbcdigit_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|číslice|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění číslic ASCII: 0x30 < =`c`< = 0x39.|
|[_ismbcgraph – _ismbcgraph_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Obrázek|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění libovolného ASCII nebo písma katakana tisknutelného znaku kromě mezery (). Viz příklady pro `_ismbcdigit`, `_ismbcalpha`, a `_ismbcpunct`.|
|[_ismbclegal – _ismbclegal_l –](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Platné vícebajtové znaky|Vrátí nenulovou hodnotu, pokud a pouze tehdy, pokud první bajt `c` je v rozsahu 0x81 – 0x9F nebo 0xE0 – 0xFC, zatímco druhý bajt je v rozsahu 0x40 – 0x7E nebo 0x80 – FC.|
|[_ismbclower – _ismbclower_l –](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Malá písmena|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění písmena malá písmena anglické abecedy ASCII: 0x61 < =`c`< = 0x7A.|
|[_ismbcprint – _ismbcprint_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Tisknutelný|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění jakékoli ASCII nebo písma katakana tisknutelný znak včetně mezery (): viz příklady pro `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha`, a `_ismbcpunct`.|
|[_ismbcpunct – _ismbcpunct_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Interpunkční znaménka|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění libovolného znaku ASCII nebo písma katakana interpunkce.|
|[_ismbcblank _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Mezera nebo horizontální tabelátor|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění znaku mezery nebo znak horizontálního tabulátoru: `c`= 0x20 nebo `c`= 0x09.|
|[_ismbcspace – _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Prázdné znaky|Vrátí nenulovou hodnotu právě tehdy `c` je prázdný znak: `c`= 0x20 nebo 0x09 < =`c`< = 0x0D.|
|[_ismbcsymbol – _ismbcsymbol_l –](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Vícebajtový symbol|Vrátí nenulovou hodnotu právě tehdy 0x8141 < =`c`< = 0x81AC.|
|[_ismbcupper – _ismbcupper_l –](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Velká písmena|Vrátí nenulovou hodnotu právě tehdy `c` je jednobajtové znázornění písmena velká písmena anglické abecedy ASCII: 0x41 < =`c`< = 0x5A.|

**Specifické pro kódovou stránku 932**

Tyto rutiny jsou specifické pro znakovou stránku 932.

|Rutina|Testovací podmínka (pouze znaková stránky 932)|
|-------------|-------------------------------------------|
|[_ismbchira – _ismbchira_l –](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Dvoubajtové znaky Hiragana: 0x829F < =`c`< = 0x82F1.|
|[_ismbckata – _ismbckata_l –](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Dvoubajtové znaky katakana: 0x8340 < =`c`< = 0x8396.|
|[_ismbcl0 – _ismbcl0_l –](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Bez JIS-Kanji: 0x8140 < =`c`< = 0x889E.|
|[_ismbcl1 – _ismbcl1_l –](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|1. úrovně JIS: 0x889F < =`c`< = 0x9872.|
|[_ismbcl2 – _ismbcl2_l –](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|2. úrovně JIS: 0x989F < =`c`< = 0xEA9E.|

`_ismbcl0`, `_ismbcl1`, a `_ismbcl2` ověří, zda zadaná hodnota `c` odpovídá zkušebním podmínkám popsaným v předchozí tabulce, ale nekontrolují, zda `c` je platný vícebajtový znak. Pokud nižší bajt je v rozsahu 0x00 – 0x3F, 0x7F nebo 0xFD – 0xFF, tyto funkce vrátí nenulovou hodnotu, která udává, že znak splňuje testovací podmínku. Použití [_ismbbtrail _ismbbtrail_l –](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) k ověření, zda je vícebajtový znak definován.

**END specifické pro kódovou stránku 932**

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../c-runtime-library/character-classification.md)<br/>
[is, isw – rutiny](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb – rutiny](../c-runtime-library/ismbb-routines.md)