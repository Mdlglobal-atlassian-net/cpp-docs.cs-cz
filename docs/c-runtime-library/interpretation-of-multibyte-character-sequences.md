---
title: "Výklad sekvencí vícebajtových znaků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.character.multibyte
dev_langs: C++
helpviewer_keywords: MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ca454b0087bd9cc1b8ded6f7b2d4ccb201373dc4
ms.sourcegitcommit: 2a5d0e9e6829150cbc22c6de3395ec13008e3266
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Výklad sekvencí vícebajtových znaků
Většina rutiny vícebajtových znaků v běhové knihovny Microsoft rozpoznat sekvencí vícebajtových znaků týkající se vícebajtové znakové stránky. Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez `_l` příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s `_l` příponu jsou shodné s tím rozdílem, že používají předaný v místo toho parametr národního prostředí.  
  
### <a name="locale-dependent-multibyte-routines"></a>Více-bajtové rutiny závislých na národním prostředí  
  
|Rutina|Použití|  
|-------------|---------|  
|[_mbclen – mblen –, _mblen_l –](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Ověření a vrátí počet bajtů v vícebajtových znaků|  
|[strlen –, wcslen –, _mbslen –, _mbslen_l –, _mbstrlen –, _mbstrlen_l –](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Řetězce vícebajtových znaků: ověření každý znak v řetězci; Vrátí délku řetězce. Široká znaková řetězce: vrátit délka řetězce.|  
|[mbstowcs –, _mbstowcs_l –](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s –, _mbstowcs_s_l –](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Převést pořadí více-bajtové znaky na odpovídající pořadí široké znaky|  
|[mbtowc –, _mbtowc_l –](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Převést na odpovídající široká znaková vícebajtových znaků|  
|[wcstombs –, _wcstombs_l –](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s –, _wcstombs_s_l –](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Převést na odpovídající pořadí více-bajtové znaky pořadí široké znaky|  
|[wctomb –, _wctomb_l –](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s –, _wctomb_s_l –](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Převést široká znaková na odpovídající vícebajtových znaků|  
|[mbrtoc16 mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Převod vícebajtových znaků na ekvivalentní UTF-16 nebo UTF-32 znaků|  
|[c16rtomb c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Převést UTF-16 nebo UTF-32 znaků na ekvivalentní vícebajtových znaků|  
  
## <a name="see-also"></a>Viz také  
 [Internacionalizace](../c-runtime-library/internationalization.md)   
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)