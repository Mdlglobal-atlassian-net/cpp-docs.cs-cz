---
title: Řetězce jazyků
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: a9e6eaa65516b5b49022526f24e220dec83b2c26
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500075"
---
# <a name="language-strings"></a>Řetězce jazyků

Funkce [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) a [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) mohou používat jazyky podporované rozhraním Windows NLS API v operačních systémech, které nepoužívají znakovou stránku Unicode. Seznam podporovaných jazyků podle verze operačního systému najdete v [příloze a: Chování](https://msdn.microsoft.com/library/cc233982.aspx) produktu v [MS-LCID]: Odkaz na identifikátor kódu jazyka systému Windows (LCID). Řetězec jazyka může být libovolná hodnota ve sloupci **jazyk** a **jazykové značky** v seznamu podporovaných jazyků. Příklad kódu, který vytváří výčet dostupných názvů národních prostředí a souvisejících hodnot, najdete v [tématu NLS: Ukázka](/windows/win32/intl/nls--name-based-apis-sample)rozhraní API založených na názvech.

## <a name="additional-supported-language-strings"></a>Další podporované řetězce jazyka

Implementace knihovny run-time jazyka C společnosti Microsoft podporuje i tyto řetězce jazyka:

|Řetězec jazyka|Ekvivalentní název národního prostředí|
|---------------------|----------------------------|
|anglického|en-US|
|americká angličtina|en-US|
|americká – angličtina|en-US|
|časopisu|cs AU|
|Lucemburské|nl-BE|
|Kanadské|cs CA|
|chh|zh-HK|
|γ2|zh-SG|
|Čínština|ZH|
|chinese-hongkong|zh-HK|
|čínština (zjednodušená)|zh-CN|
|čínština – Singapur|zh-SG|
|čínština (tradiční)|zh-TW|
|Holandština – belgické|nl-BE|
|Angličtina – americká|en-US|
|Angličtina (Austrálie)|cs AU|
|Angličtina – Belize|en-BZ|
|Angličtina – může|cs CA|
|Angličtina (Karibská oblast)|en-029|
|Angličtina – vyžadovat|cs IE|
|Angličtina – Jamajka|EN-JM|
|english-nz|cs NZ|
|Angličtina (Jihoafrická Korea)|EN-ZA|
|Angličtina – Trinidad a Tobago|en-TT|
|Angličtina (Velká Británie)|en-GB|
|Angličtina (USA)|en-US|
|Angličtina (USA)|en-US|
|francouzština – Belgie|fr – bude|
|francouzština (Kanada)|fr-CA|
|francouzština – Lucembursko|fr-LU|
|francouzština (Švýcarsko)|FR-CH|
|Němčina – Rakousko|de-AT|
|Němčina – Lichtenstein|de-LI|
|Němčina – Lucembursko|de-LU|
|german-swiss|de-CH|
|Irština – angličtina|cs IE|
|Italština – Švýcarsko|IT – CH|
|Norština|Ne|
|Norština – Bokmal|nb-NO|
|Norština – Nynorsk|NN – ne|
|portugalština – Brazílie|pt-BR|
|Španělština – Argentina|ES-AR|
|španělština a Bolívie|es-BO|
|Španělština – Chile|es-CL|
|Španělština – Kolumbie|es-CO|
|Španělština – Kostarika|es-CR|
|Španělština – Dominikánská republika|es-DO|
|Španělština – Ekvádor|es-EC|
|Španělština (Salvador)|es-SV|
|Španělština – Guatemala|es-GT|
|spanish-honduras|es-HN|
|Španělština – Mexiko|es-MX|
|Španělština – moderní|es-ES|
|Španělština – Nikaragua|es-NI|
|Španělština – Panama|es-PA|
|Španělština – Paraguay|ES – PY|
|Španělština – Peru|es-PE|
|Španělština – Portoriko|es-PR|
|Španělština – Uruguay|es-UY|
|Španělština – Venezuela|es-VE|
|Švédština – Finsko|sv-FI|
|Švýcarské|de-CH|
|Velká Británie|en-GB|
|vylepšení|en-US|
|usa|en-US|

## <a name="see-also"></a>Viz také:

[Názvy národních prostředí, jazyky a řetězce země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Řetězce země/oblasti](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
