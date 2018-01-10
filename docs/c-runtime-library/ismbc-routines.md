---
title: "_ismbc – rutiny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords: _ismbc
dev_langs: C++
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cbe2879f031f261871676f9e11f0b6f2a0908a95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ismbc-routines"></a>_ismbc – rutiny
Každý **_ismbc –** rutiny testy dané vícebajtových znaků `c` pro určitá podmínka.  
  
|||  
|-|-|  
|[_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0, _ismbcl0_l, _ismbcl1, _ismbcl1_l, _ismbcl2, _ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|  
|[_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal, _ismbclegal_l, _ismbcsymbol, _ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|  
|[_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|  
  
## <a name="remarks"></a>Poznámky  
 Výsledek testu jednotlivých **_ismbc –** rutiny závisí na vícebajtové znakové stránky v platnosti. Vícebajtové znakové stránky mít jednobajtové znaky abecedy. Vícebajtové znakové stránky je standardně nastavena na výchozí systémová znaková stránka ANSI získané z operačního systému při spuštění programu. Můžete zadat dotaz nebo změnit vícebajtové znakové stránky používají s [_getmbcp –](../c-runtime-library/reference/getmbcp.md) nebo [_setmbcp](../c-runtime-library/reference/setmbcp.md), v uvedeném pořadí.  
  
 Výstupní hodnota je ovlivňován `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná.  
  
|Rutina|Test stavu|Příklad kódu stránka 932|  
|-------------|--------------------|---------------------------|  
|[_ismbcalnum –, _ismbcalnum_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumerické|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové k písmenu anglické ASCII: obsahuje příklady `_ismbcdigit` a `_ismbcalpha`.|  
|[_ismbcalpha –, _ismbcalpha –\_](../c-runtime-library/reference/ismbcalnum-functions.md)|Abecedy|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové k písmenu anglické ASCII: obsahuje příklady `_ismbcupper` a `_ismbclower`; nebo katakana písmeno: 0xA6 < =`c`< = 0xDF.|  
|[_ismbcdigit –, _ismbcdigit_l –](../c-runtime-library/reference/ismbcalnum-functions.md)|Číslice|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové číslic ASCII: 0x30 < =`c`< = 0x39.|  
|[_ismbcgraph –, _ismbcgraph_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Obrázek|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové jakémukoli ASCII nebo katakana tisknutelná znaku kromě () mezer. Obsahuje příklady `_ismbcdigit`, `_ismbcalpha`, a `_ismbcpunct`.|  
|[_ismbclegal –, _ismbclegal_l –](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Platný vícebajtových znaků|Vrátí první bajt nenulové hodnoty v případě a pouze v případě `c` je v rámci rozsahy 0x81-0x9F nebo 0xE0 - 0xFC, zatímco druhý bajt je v rámci rozsahy 0x40-0x7E nebo 0x80 - FC.|  
|[_ismbclower –, _ismbclower_l –](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Malá písmena|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové k ASCII písmenu malá písmena anglické: 0x61 < =`c`< = 0x7A.|  
|[_ismbcprint –, _ismbcprint_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Tisknutelná|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové libovolný ASCII nebo katakana tisknutelná znak včetně () mezer: obsahuje příklady `_ismbcspace`, `_ismbcdigit`, `_ismbcalpha`, a `_ismbcpunct`.|  
|[_ismbcpunct –, _ismbcpunct_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Interpunkční znaménka|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové žádné ASCII nebo katakana interpunkční znaménko.|  
|[_ismbcblank, _ismbcblank_l,](../c-runtime-library/reference/ismbcgraph-functions.md)|Místo nebo vodorovné karta|Vrátí nenulové hodnoty v případě a pouze v případě `c` je jednobajtové reprezentace znak mezery nebo vodorovné tabulátorem: `c`= 0x20 nebo `c`= 0x09.|  
|[_ismbcspace –, _ismbcspace_l –](../c-runtime-library/reference/ismbcgraph-functions.md)|Prázdné znaky|Vrátí nenulové hodnoty v případě a pouze v případě `c` je prázdný znak: `c`= 0x20 nebo 0x09 < =`c`< = 0x0D.|  
|[_ismbcsymbol –, _ismbcsymbol_l –](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Více-bajtové – symbol|Vrátí nenulové hodnoty v případě a pouze v případě 0x8141 < =`c`< = 0x81AC.|  
|[_ismbcupper –, _ismbcupper_l –](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Velká písmena|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové velkým písmenem ASCII anglické: 0x41 < =`c`< = 0x5A.|  
  
 **Kód konkrétní stránka 932**  
  
 Následující rutiny jsou specifické pro znaková stránka 932.  
  
|Rutina|Test stavu (pouze znaková stránka 932)|  
|-------------|-------------------------------------------|  
|[_ismbchira –, _ismbchira_l –](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Dvoubajtové Hiragana: 0x829F < =`c`< = 0x82F1.|  
|[_ismbckata –, _ismbckata_l –](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Dvoubajtové katakana: 0x8340 < =`c`< = 0x8396.|  
|[_ismbcl0 –, _ismbcl0_l –](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Bez JIS-Kanji: 0x8140 < =`c`< = 0x889E.|  
|[_ismbcl1 –, _ismbcl1_l –](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Úroveň 1 JIS: 0x889F < =`c`< = 0x9872.|  
|[_ismbcl2 –, _ismbcl2_l –](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Úroveň 2 JIS: 0x989F < =`c`< = 0xEA9E.|  
  
 `_ismbcl0`, `_ismbcl1`, a `_ismbcl2` zkontrolujte, zda zadaná hodnota `c` odpovídá podmínky testu popsané v předchozím tabulky, ale není, zkontrolujte `c` je platný vícebajtových znaků. Pokud nižší bajt je v oblastech 0x00-0x3F, 0x7F nebo 0xFD - 0xFF, tyto funkce vrátí nenulovou hodnotu, která určuje, že znak, který splňuje podmínky testu. Použití [_ismbbtrail –, _ismbbtrail_l –](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) k ověření, zda je definována vícebajtových znaků.  
  
 **END kódu konkrétní stránka 932**  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../c-runtime-library/character-classification.md)   
 [je, isw – rutiny](../c-runtime-library/is-isw-routines.md)   
 [_ismbb – rutiny](../c-runtime-library/ismbb-routines.md)