---
title: Text a řetězce v jazyce Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
ms.openlocfilehash: 80b7139996fddc82b206828d4a036922fa1446d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167599"
---
# <a name="text-and-strings-in-visual-c"></a>Text a řetězce v jazyce Visual C++

Důležitým aspektem vývoje aplikací pro mezinárodní trhy je odpovídající reprezentace místních znakových sad. Znaková sada ASCII definuje znaky v rozsahu 0x00 až 0x7F. Existují i jiné znakové sady, které definují znaky v rozsahu 0x00 až 0x7F stejným způsobem jako znaková sada ASCII a také definují rozšířenou znakovou sadu z 0x80 na 0xFF. Proto je 16bitová Vícebajtová znaková sada (SBCS) dostačující pro reprezentaci znakové sady ASCII a také znakové sady pro mnoho evropských jazyků. Nicméně některé neevropské znakové sady, například japonské kanji, obsahují mnoho dalších znaků, než je jednobajtové schéma kódování, může představovat, a proto vyžaduje kódování vícebajtových znakových sad (MBCS).

## <a name="in-this-section"></a>V tomto oddílu

[Unicode a MBCS](../text/unicode-and-mbcs.md)<br/>
Popisuje vizuální C++ podporu programování Unicode a MBCS.

[Podpora pro Unicode](../text/support-for-unicode.md)<br/>
Popisuje znakovou sadu Unicode, specifikaci pro podporu všech znakových sad, včetně znakových sad, které nemohou být reprezentovány v jednom bajtu.

[Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
Popisuje znakovou sadu MBCS, alternativu ke znakové sadě Unicode pro podpůrné znakové sady, jako je například japonština a čínština, které nemohou být reprezentovány v jednom bajtu.

[Mapování obecného textu v souboru tchar.h](../text/generic-text-mappings-in-tchar-h.md)<br/>
Poskytuje mapování obecného textu specifického pro společnost Microsoft pro mnoho datových typů, rutin a dalších objektů.

[Postupy: Převody mezi různými typy řetězců](../text/how-to-convert-between-various-string-types.md)<br/>
Ukazuje, jak převést různé typy C++ vizuálních řetězců na jiné řetězce.

## <a name="related-sections"></a>Související oddíly

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
Popisuje mezinárodní podporu v knihovně run-time jazyka C.

[Mezinárodní ukázky](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International)<br/>
Obsahuje odkazy na ukázky, které demonstrují mezinárodní C++využití v vizuálu.

[Řetězce jazyka a země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
Poskytuje řetězce jazyka a země/oblasti v knihovně run-time jazyka C.
