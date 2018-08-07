---
title: Řetězce jazyků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eaab56876651a1056ef89d57bebb2799d1bb3194
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604138"
---
# <a name="language-strings"></a>Řetězce jazyků

[Setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) a [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) funkce můžete použít rozhraní API Windows NLS podporované jazyky operačních systémů, které nepoužívají znakovou stránku kódování Unicode. Seznam podporovaných jazyků podle verze operačního systému najdete v tématu [chování produktu dodatku A:](https://msdn.microsoft.com/library/cc233982.aspx) v [MS-LCID]: odkaz na identifikátor pro kód jazyka Windows (LCID). Řetězec jazyka může nabývat hodnoty v **jazyk** a **značku jazyka** sloupce seznam podporovaných jazyků. Příklad kódu, který vytvoří výčet dostupných názvů národního prostředí a souvisejících hodnot najdete v tématu [NLS: Ukázka rozhraní API na základě názvu](/windows/desktop/intl/nls--name-based-apis-sample).

## <a name="additional-supported-language-strings"></a>Další podporovaných řetězců jazyka

Implementace knihovny runtime jazyka Microsoft C podporuje také tyto řetězce jazyka:

|Řetězec jazyka|Odpovídající místní název|
|---------------------|----------------------------|
|American|en US|
|americkou angličtinu|en US|
|americkou angličtinu|en US|
|Australský|cs AU|
|Belgie|nl-BE|
|Kanadský|cs CA|
|CHH|zh-HK|
|Kuba|zh-SG|
|Čínština|zh|
|čínština hongkong|zh-HK|
|čínština (zjednodušená)|zh-CN|
|Čínština – Singapur|zh-SG|
|čínština (tradiční)|zh-TW|
|Holandština – Belgie|nl-BE|
|americká angličtina|en US|
|Angličtina – Austrálie|cs AU|
|Angličtina – belize|en BZ|
|angličtina, může|cs CA|
|Angličtina – Karibská oblast|cs-029|
|vyžadovat angličtina|cs IE|
|Angličtina – Jamajka|cs JM|
|nz – angličtina|cs NZ|
|Angličtina – Jihoafrická republika|cs ZA|
|Angličtina – trinidad a tobago|cs TT|
|angličtina – Velká Británie|en-GB|
|Angličtina-USA|en US|
|Angličtina usa|en US|
|Francouzština – Belgie|FR-být|
|French-Canadian|fr-CA|
|Francouzština – Lucembursko|FR LU|
|Francouzština – Švýcarsko|FR-CH|
|Němčina – Rakousko|de-AT|
|Němčina – lichtenstein|de-LI|
|Němčina – Lucembursko|de-LU|
|Němčina – Švýcarsko|de-CH|
|Irština – angličtina|cs IE|
|Italština – Švýcarsko|IT CH|
|Norština|Ne|
|Norština – bokmal|nb-NO|
|norština – nynorsk|nn – ne|
|Brazilská portugalština|pt-BR|
|Španělština – argentina|ES AR|
|Španělština – Bolívie|ES BO|
|Španělština – chile|ES-CL|
|Španělština – Kolumbie|ES CO|
|Španělština – Kostarika|ES CR|
|Španělština – Dominikánská republika|Proveďte ES|
|Španělština – Ekvádor|ES ES|
|Španělština – el salvador|ES SV|
|Španělština – guatemala|ES-GT|
|Španělština – honduras|ES HN|
|Španělština – Mexiko|es-MX|
|španělština – moderní|es-ES|
|Španělština – Nikaragua|ES-NI|
|Španělština – panama|ES PA|
|Španělština – paraguay|ES-PY|
|Španělština – peru|ES-PE|
|Španělština – Portoriko|ES – žádost o přijetí změn|
|Španělština – uruguay|ES UY|
|Španělština – venezuela|ES – odebrat|
|Švédština – Finsko|sv-FI|
|Švýcarsko|de-CH|
|Spojené království|en-GB|
|USA|en US|
|USA|en US|

## <a name="see-also"></a>Viz také:

[Názvy národních prostředí, jazyků a Country/Region Strings](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
[Řetězce zemí/oblastí](../c-runtime-library/country-region-strings.md)  
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)  
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)  
