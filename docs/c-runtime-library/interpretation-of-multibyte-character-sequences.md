---
title: Výklad sekvencí vícebajtových znaků | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- c.character.multibyte
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d52a8b3572f398a97c902cf0bcd647a3752cee8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Výklad sekvencí vícebajtových znaků

Většina rutiny vícebajtových znaků v běhové knihovny Microsoft rozpoznat sekvencí vícebajtových znaků týkající se vícebajtové znakové stránky. Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná.

## <a name="locale-dependent-multibyte-routines"></a>Více-bajtové rutiny závislých na národním prostředí

|Rutina|Použití|
|-------------|---------|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Ověření a vrátí počet bajtů v vícebajtových znaků|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Řetězce vícebajtových znaků: ověření každý znak v řetězci; Vrátí délku řetězce. Široká znaková řetězce: vrátit délka řetězce.|
|[mbstowcs –, _mbstowcs_l –](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s –, _mbstowcs_s_l –](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Převést pořadí více-bajtové znaky na odpovídající pořadí široké znaky|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Převést na odpovídající široká znaková vícebajtových znaků|
|[wcstombs –, _wcstombs_l –](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s –, _wcstombs_s_l –](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Převést na odpovídající pořadí více-bajtové znaky pořadí široké znaky|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Převést široká znaková na odpovídající vícebajtových znaků|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Převod vícebajtových znaků na ekvivalentní UTF-16 nebo UTF-32 znaků|
|[c16rtomb c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Převést UTF-16 nebo UTF-32 znaků na ekvivalentní vícebajtových znaků|

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
 [Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
