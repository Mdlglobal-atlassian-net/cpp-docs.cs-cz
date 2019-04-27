---
title: Řetězce jazyků
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 143f06a0cf22265734d6d77f8fca4efd5ac3031b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343144"
---
# <a name="language-strings"></a>Řetězce jazyků

[Setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) a [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) funkce můžete použít rozhraní API Windows NLS podporované jazyky operačních systémů, které nepoužívají znakovou stránku kódování Unicode. Seznam podporovaných jazyků podle verze operačního systému najdete v tématu [dodatku A: Chování produktu](https://msdn.microsoft.com/library/cc233982.aspx) v [MS-LCID]: Odkaz na identifikátor (LCID) kód jazyka Windows. Řetězec jazyka může nabývat hodnoty v **jazyk** a **značku jazyka** sloupce seznam podporovaných jazyků. Příklad kódu, který vytvoří výčet dostupných názvů národního prostředí a souvisejících hodnot najdete v tématu [NLS: Ukázka rozhraní API na základě názvu](/windows/desktop/intl/nls--name-based-apis-sample).

## <a name="additional-supported-language-strings"></a>Další podporovaných řetězců jazyka

Implementace knihovny runtime jazyka Microsoft C podporuje také tyto řetězce jazyka:

|Řetězec jazyka|Odpovídající místní název|
|---------------------|----------------------------|
|American|en-US|
|americkou angličtinu|en-US|
|americkou angličtinu|en-US|
|Australský|cs AU|
|Belgie|nl-BE|
|Kanadský|cs CA|
|CHH|zh-HK|
|chi|zh-SG|
|Čínština|zh|
|chinese-hongkong|zh-HK|
|čínština (zjednodušená)|zh-CN|
|Čínština – Singapur|zh-SG|
|čínština (tradiční)|zh-TW|
|Holandština – Belgie|nl-BE|
|americká angličtina|en-US|
|Angličtina – Austrálie|cs AU|
|Angličtina – belize|en-BZ|
|angličtina, může|cs CA|
|Angličtina – Karibská oblast|en-029|
|vyžadovat angličtina|cs IE|
|Angličtina – Jamajka|cs JM|
|english-nz|cs NZ|
|Angličtina – Jihoafrická republika|en-ZA|
|Angličtina – trinidad a tobago|en-TT|
|angličtina – Velká Británie|en-GB|
|Angličtina-USA|en-US|
|Angličtina usa|en-US|
|Francouzština – Belgie|fr-BE|
|French-Canadian|fr-CA|
|Francouzština – Lucembursko|fr-LU|
|Francouzština – Švýcarsko|FR-CH|
|Němčina – Rakousko|de-AT|
|german-lichtenstein|de-LI|
|Němčina – Lucembursko|de-LU|
|german-swiss|de-CH|
|Irština – angličtina|cs IE|
|italian-swiss|it-CH|
|Norština|Ne|
|Norština – bokmal|nb-NO|
|norwegian-nynorsk|nn – ne|
|Brazilská portugalština|pt-BR|
|Španělština – argentina|es-AR|
|Španělština – Bolívie|es-BO|
|Španělština – chile|es-CL|
|Španělština – Kolumbie|es-CO|
|Španělština – Kostarika|es-CR|
|Španělština – Dominikánská republika|es-DO|
|Španělština – Ekvádor|es-EC|
|Španělština – el salvador|es-SV|
|Španělština – guatemala|es-GT|
|spanish-honduras|es-HN|
|Španělština – Mexiko|es-MX|
|španělština – moderní|es-ES|
|Španělština – Nikaragua|es-NI|
|Španělština – panama|es-PA|
|Španělština – paraguay|es-PY|
|Španělština – peru|es-PE|
|Španělština – Portoriko|es-PR|
|Španělština – uruguay|es-UY|
|Španělština – venezuela|es-VE|
|swedish-finland|sv-FI|
|Švýcarsko|de-CH|
|Spojené království|en-GB|
|USA|en-US|
|usa|en-US|

## <a name="see-also"></a>Viz také:

[Názvy národních prostředí, jazyků a Country/Region Strings](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Řetězce zemí/oblastí](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
