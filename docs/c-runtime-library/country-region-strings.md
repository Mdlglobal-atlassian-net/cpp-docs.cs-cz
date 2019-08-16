---
title: Řetězce oblasti země
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 49eb6bc4473d9e54c06c3bf9290f8c3c96640415
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500247"
---
# <a name="countryregion-strings"></a>Řetězce zemí/oblastí

Řetězce země a oblasti mohou být kombinovány s řetězcem jazyka pro vytvoření specifikace národního prostředí pro `setlocale`funkce `_wsetlocale`, `_create_locale`, a `_wcreate_locale` . Seznamy názvů zemí a oblastí, které jsou podporovány různými verzemi operačního systému Windows, naleznete v části **jazyk**, **umístění**a sloupce **značek jazyka** v tabulce v [příloze A: Chování](https://msdn.microsoft.com/library/cc233982.aspx) produktu v [MS-LCID]: Odkaz na identifikátor kódu jazyka systému Windows (LCID). Příklad kódu, který vytváří výčet dostupných názvů národních prostředí a souvisejících hodnot, najdete v [tématu NLS: Ukázka](/windows/win32/intl/nls--name-based-apis-sample)rozhraní API založených na názvech.

## <a name="additional-supported-country-and-region-strings"></a>Další podporované řetězce země a oblasti

Implementace knihovny runtime jazyka C společnosti Microsoft podporuje také následující další řetězce a zkratky země/oblasti:

|Řetězec země/oblasti|Zkratka|Ekvivalentní název národního prostředí|
|----------------------------|------------------|----------------------------|
|používaný|USA|en-US|
|Británie|GBR|en-GB|
|lidov|CHN|zh-CN|
|Čeština|CZE|cs-CZ|
|až|GBR|en-GB|
|Velká Británie|GBR|en-GB|
|Holland|NLD|NL-NL|
|hong-kong|HKG|zh-HK|
|Nový Zéland|NZL|cs NZ|
|nz|NZL|cs NZ|
|PR – Čína|CHN|zh-CN|
|PR – Čína|CHN|zh-CN|
|puerto-rico|PRI|es-PR|
|Slovenština|SVK|sk-SK|
|Jihoafrická republika|ZAF|af-ZA|
|Jižní Korea|KOR|ko-KR|
|Jižní Afrika|ZAF|af-ZA|
|Jižní Korea|KOR|ko-KR|
|Trinidad & Tobago|TTO|en-TT|
|Velká Británie|GBR|en-GB|
|Spojené království|GBR|en-GB|
|Spojené státy|USA|en-US|
|vylepšení|USA|en-US|

## <a name="see-also"></a>Viz také:

[Názvy národních prostředí, jazyky a řetězce země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Řetězce jazyků](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
