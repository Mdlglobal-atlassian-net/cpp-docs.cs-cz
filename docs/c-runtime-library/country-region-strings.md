---
title: Řetězce oblasti země
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 8556e005618a1b69c47498a07e218284dcb1164f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443433"
---
# <a name="countryregion-strings"></a>Řetězce zemí/oblastí

Řetězce země a oblasti mohou být kombinovány s řetězcem jazyka pro vytvoření specifikace národního prostředí pro `setlocale`, `_wsetlocale`, `_create_locale`a `_wcreate_locale` funkcí. Seznamy názvů zemí a oblastí, které jsou podporovány různými verzemi operačního systému Windows, naleznete v části **jazyk**, **umístění**a sloupce **značek jazyka** v tabulce v [příloze A: chování produktu](https://msdn.microsoft.com/library/cc233982.aspx) v [MS-LCID]: odkaz na identifikátor kódu jazyka Windows (LCID). Příklad kódu, který vytváří výčet dostupných názvů národních prostředí a souvisejících hodnot, naleznete v části [NLS: název rozhraní API na základě názvů](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Další podporované řetězce země a oblasti

Implementace knihovny runtime jazyka C společnosti Microsoft podporuje také následující další řetězce a zkratky země/oblasti:

|Řetězec země/oblasti|Zkratka|Ekvivalentní název národního prostředí|
|----------------------------|------------------|----------------------------|
|Používaný|USA|cs-CZ|
|Británie|GBR|en-GB|
|Lidov|CHN|zh-CN|
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
|Spojené státy|USA|cs-CZ|
|vylepšení|USA|cs-CZ|

## <a name="see-also"></a>Viz také

[Názvy národních prostředí, jazyky a řetězce země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Řetězce jazyků](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
