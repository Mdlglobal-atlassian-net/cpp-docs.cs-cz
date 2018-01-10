---
title: "_ismbb – rutiny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad7e454af3ff8923d60315cd74d48daf9bd665a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ismbb-routines"></a>_ismbb – rutiny
Testy dané celočíselná hodnota `c` pro určitá podmínka, pomocí aktuální národní prostředí nebo zadané kategorii LC_CTYPE – převod stavu.  
  
|||  
|-|-|  
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|  
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|  
|[_ismbbblank, _ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|  
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|  
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|  
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|  
  
## <a name="remarks"></a>Poznámky  
 Každou rutinu v `_ismbb` rodiny testy dané celočíselná hodnota `c` pro určitá podmínka. Výsledek testu závisí na vícebajtové znakové stránky, který je v platnosti. Vícebajtové znakové stránky je standardně nastavena na stránku ANSI kód, který byl získán z operačního systému při spuštění programu. Můžete použít [_getmbcp –](../c-runtime-library/reference/getmbcp.md) k dotazování vícebajtové znakové stránky, která se používá, nebo [_setmbcp](../c-runtime-library/reference/setmbcp.md) ho změnit.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; Další informace najdete v části [setlocale _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Verze tyto funkce, které nemají **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze, které mají **_l** příponu jsou identické s výjimkou, že místo toho budou použijte parametr národního prostředí, který se předává v.  
  
 Rutiny v `_ismbb` rodiny testování dané celé číslo `c` následujícím způsobem.  
  
|Rutina|Stav testu bajtů|  
|-------------|-------------------------|  
|[_ismbbalnum –](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbalpha –](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|  
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|  
|[_ismbbgraph –](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Stejné jako `_ismbbprint`, ale `_ismbbgraph` neobsahuje znak mezery (0x20).|  
|[_ismbbkalnum –](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Symbol text ASCII jiného typu než interpunkce. Například v pouze znaková stránka 932 `_ismbbkalnum` testů pro katakana alfanumerické znaky.|  
|[_ismbbkana –](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana (0xA1 - 0xDF). Specifické pro znaková stránka 932.|  
|[_ismbbkprint –](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Jiné než ASCII text nebo jiné sady než ASCII interpunkční symbol. Například v pouze znaková stránka 932 `_ismbbkprint` testů pro katakana alfanumerické nebo katakana interpunkce (rozsah: 0xA1 - 0xDF).|  
|[_ismbbkpunct –](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Interpunkce non-ASCII. Například v pouze znaková stránka 932 `_ismbbkpunct` testů pro katakana interpunkce.|  
|[_ismbblead –](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|První bajt vícebajtových znaků. Například v kódu stránky 932 pouze, platné rozsahy jsou 0x81 - 0x9F, 0xE0 - 0xFC.|  
|[_ismbbprint –](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint –** obsahuje znak mezery (0x20).|  
|[_ismbbpunct –](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|  
|[_ismbbtrail –](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Druhý bajt vícebajtových znaků. Například v kódu stránky 932 pouze, platné rozsahy jsou 0x40 - 0x7E, 0x80 - 0xEC.|  
  
 V následující tabulce jsou uvedeny ORed hodnoty, které tvoří podmínky testu pro tyto rutiny. Manifestu konstanty `_BLANK`, `_DIGIT`, `_LOWER`, `_PUNCT`, a `_UPPER` jsou definovány v Ctype.h.  
  
|Rutina|_BLANK|_DIGIT|NIŽŠÍ|_PUNCT|HORNÍ|Jinou hodnotu než<br /><br /> ASCII<br /><br /> text|Jinou hodnotu než<br /><br /> ASCII<br /><br /> punct|  
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
  
 `_ismbb` Rutiny jsou implementované jako funkce i jako makra. Další informace o tom, jak zvolit buď implementace najdete v tématu [doporučení pro výběr mezi funkcemi a makry](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace bajtů](../c-runtime-library/byte-classification.md)   
 [je, isw – rutiny](../c-runtime-library/is-isw-routines.md)   
 [_mbbtombc –, _mbbtombc_l –](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)