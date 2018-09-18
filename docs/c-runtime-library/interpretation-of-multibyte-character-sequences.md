---
title: Výklad sekvencí vícebajtových znaků | Dokumentace Microsoftu
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
ms.openlocfilehash: 86fc93b74f661ac0829c0ed5925cb9cf78a8876e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103630"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Výklad sekvencí vícebajtových znaků

Většina rutin vícebajtového znaku v běhové knihovny Microsoft rozpoznat vícebajtové znakové sekvence pro vícebajtové znakové stránky. Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze těchto funkcí bez **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí; verze s **_l** přípona jsou stejné s tím rozdílem, že používají parametr národního prostředí místo něho předán v.

## <a name="locale-dependent-multibyte-routines"></a>Rutiny pro vícebajtové závislé na národním prostředí

|Rutina|Použití|
|-------------|---------|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Ověření a vrátí počet bajtů ve vícebajtové znaky|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Pro vícebajtové znakové řetězce: ověření každý znak v řetězci; Vrátí délku řetězce. Pro řetězce širokého znaku: vrátí délku řetězce.|
|[mbstowcs _mbstowcs_l –](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s _mbstowcs_s_l –](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Převod sekvence vícebajtových znaků na odpovídající pořadí širokých znaků|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Převést vícebajtový znak na odpovídající široké znaky|
|[wcstombs – _wcstombs_l –](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s – _wcstombs_s_l –](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Převod sekvence širokých znaků na odpovídající sekvence vícebajtových znaků|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Převést na odpovídající vícebajtový znak širokého znaku|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Převod vícebajtových znaků na ekvivalentní znaků UTF-16 nebo UTF-32|
|[c16rtomb c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Převést na ekvivalentní vícebajtové znakové kódování UTF-16 nebo UTF-32 znaků|

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
