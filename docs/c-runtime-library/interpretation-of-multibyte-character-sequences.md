---
title: Výklad sekvencí vícebajtových znaků
ms.date: 10/22/2019
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
ms.openlocfilehash: 7431f0c63df60414af192ea38103318c775c430d
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811085"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>Výklad sekvencí vícebajtových znaků

Většina rutin vícebajtových znaků v knihovně run-time společnosti Microsoft rozpozná vícebajtové znakové sekvence týkající se vícebajtové znakové stránky. Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí. Další informace naleznete v tématu [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Verze těchto funkcí bez přípony **_l** používají aktuální národní prostředí pro toto chování závislé na národním prostředí. Verze s příponou **_l** jsou identické, s výjimkou použití parametru locale namísto aktuálního národního prostředí.

## <a name="locale-dependent-multibyte-routines"></a>Vícebajtové rutiny závislé na národním prostředí

|Rutina|Použití|
|-------------|---------|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Ověří a vrátí počet bajtů v vícebajtovém znaku.|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Pro vícebajtové znakové řetězce: Ověřte každý znak v řetězci; Délka návratového řetězce Pro řetězce s velkým znakem: návratová délka řetězce.|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Převede sekvenci vícebajtových znaků na odpovídající sekvenci velkých znaků.|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Převést vícebajtový znak na odpovídající široce velký znak|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Převede sekvenci velkých znaků na odpovídající sekvenci vícebajtových znaků.|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Převést velký znak na odpovídající vícebajtový znak|

## <a name="locale-independent-multibyte-routines"></a>Vícebajtové rutiny nezávislé na národním prostředí

|Rutina|Použití|
|-------------|---------|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Převést vícebajtový znak UTF-8 na ekvivalentní znak UTF-16 nebo UTF-32|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Převést znak UTF-16 nebo UTF-32 na ekvivalentní vícebajtový znak UTF-8|

## <a name="see-also"></a>Viz také:

\ pro [mezinárodní využití](../c-runtime-library/internationalization.md)
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)
