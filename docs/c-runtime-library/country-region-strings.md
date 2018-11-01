---
title: Řetězce zemí / oblastí
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 3a3bbe9d1278cf733bafbeb23efcb0a1ad577228
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463463"
---
# <a name="countryregion-strings"></a>Řetězce zemí/oblastí

Řetězce země a oblasti lze kombinovat s řetězcem jazyka k vytvoření specifikace pro národní prostředí pro `setlocale`, `_wsetlocale`, `_create_locale`, a `_wcreate_locale` funkce. Seznamy názvů zemí a oblastí, které jsou podporovány v různých verzích operačního systému Windows, najdete v článku **jazyk**, **umístění**, a **značku jazyka** sloupce tabulky v [chování produktu dodatku A:](https://msdn.microsoft.com/library/cc233982.aspx) v [MS-LCID]: odkaz na identifikátor pro kód jazyka Windows (LCID). Příklad kódu, který vytvoří výčet dostupných názvů národního prostředí a souvisejících hodnot najdete v tématu [NLS: Ukázka rozhraní API na základě názvu](/windows/desktop/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Další podporovaných řetězců země a oblasti

Implementace knihovny runtime jazyka Microsoft C podporuje také následující další země/oblast řetězce a zkratky:

|Řetězec země/oblasti|Zkratka|Odpovídající místní název|
|----------------------------|------------------|----------------------------|
|Americké|USA|en US|
|Británie|GBR|en-GB|
|Čína|CHN|zh-CN|
|Čeština|CZE|cs-CZ|
|Anglii|GBR|en-GB|
|Velká Británie|GBR|en-GB|
|holland|NLD|NL-NL|
|Hongkong –|HKG|zh-HK|
|Nový Zéland|NZL|cs NZ|
|Nz|NZL|cs NZ|
|Čína (LR)|CHN|zh-CN|
|žádost o přijetí změn – Čína|CHN|zh-CN|
|– Portoriko|PRI|ES – žádost o přijetí změn|
|Slovenština|SVK|sk-SK|
|Jihoafrická republika|ZAF|af ZA|
|korea – jih|KOR|ko-KR|
|Jižní Afrika|ZAF|af ZA|
|korea – jih|KOR|ko-KR|
|Trinidad a tobago|CHCETE-LI|cs TT|
|Spojené království|GBR|en-GB|
|Spojené království|GBR|en-GB|
|Spojené státy|USA|en US|
|USA|USA|en US|

## <a name="see-also"></a>Viz také:

[Názvy národních prostředí, jazyků a Country/Region Strings](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Řetězce jazyků](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
