---
title: Řetězce jazyků
ms.date: 11/04/2016
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 18a94d33f9ca382bb6c7cd77a4f2b33ed800f2c6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438248"
---
# <a name="language-strings"></a>Řetězce jazyků

Funkce [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) a [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) můžou používat jazyky podporované rozhraním Windows NLS API v operačních systémech, které nepoužívají znakovou stránku Unicode. Seznam podporovaných jazyků podle verze operačního systému najdete v [příloze a: chování produktu](https://msdn.microsoft.com/library/cc233982.aspx) v [MS-LCID]: referenční informace k identifikátoru kódu jazyka Windows (LCID). Řetězec jazyka může být libovolná hodnota ve sloupci **jazyk** a **jazykové značky** v seznamu podporovaných jazyků. Příklad kódu, který vytváří výčet dostupných názvů národních prostředí a souvisejících hodnot, naleznete v části [NLS: název rozhraní API na základě názvů](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-language-strings"></a>Další podporované řetězce jazyka

Implementace knihovny run-time jazyka C společnosti Microsoft podporuje i tyto řetězce jazyka:

|Řetězec jazyka|Ekvivalentní název národního prostředí|
|---------------------|----------------------------|
|anglického|cs-CZ|
|americká angličtina|cs-CZ|
|americká – angličtina|cs-CZ|
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
|Angličtina – americká|cs-CZ|
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
|Angličtina (USA)|cs-CZ|
|Angličtina (USA)|cs-CZ|
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
|Norština|ne|
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
|vylepšení|cs-CZ|
|usa|cs-CZ|

## <a name="see-also"></a>Viz také

[Názvy národních prostředí, jazyky a řetězce země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Řetězce země/oblasti](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
