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
ms.openlocfilehash: bb658db157433aadce183e7fab437f15251ff54c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631293"
---
# <a name="text-and-strings-in-visual-c"></a>Text a řetězce v jazyce Visual C++

Důležitou součástí vývoje aplikací pro mezinárodní trhy je odpovídající reprezentace místní znakové sady. Znaková sada ASCII definuje znaky v rozsahu 0x00 do 0x7F. Existují jiné znakové sady, především Evropské, které definují znaky v rozsahu 0x00 do 0x7F stejně jako znaková sada ASCII a také definovat rozšířené znakové od 0x80 do 0xFF. Proto 8 bitů, jedním jednobajtového znaku sady (SBCS) je dostačující k reprezentaci znakové sady ASCII, jakož i znakových sad mnoha evropských jazyků. Ale některé neevropské znakových sad, jako je například japonská Kanji obsahovat mnoho více znaků, než schéma kódování jednobajtové představují a proto vyžadují vícebajtové znakové sady (MBCS s) kódováním.

## <a name="in-this-section"></a>V tomto oddílu

[Unicode a MBCS](../text/unicode-and-mbcs.md)<br/>
Tento článek popisuje podporu Visual C++ pro programování v kódování Unicode a MBCS.

[Podpora pro Unicode](../text/support-for-unicode.md)<br/>
Popisuje kódování Unicode, specifikace pro podporu všech znakových sad, včetně znakových sad, které nelze reprezentovat jediným bajtem.

[Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
Tento článek popisuje znakové sady MBCS, o alternativu k kódování Unicode pro podporu znakové sady, jako například japonštinu a čínštinu, které nelze reprezentovat jediným bajtem.

[Mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md)<br/>
Mapování obecného textu specifické pro společnost Microsoft poskytuje pro mnoho typů dat, rutiny a dalších objektů.

[Postupy: Převody mezi různými typy řetězců](../text/how-to-convert-between-various-string-types.md)<br/>
Ukazuje, jak převést různé řetězcové typy jazyka Visual C++ do jiných řetězců.

## <a name="related-sections"></a>Související oddíly

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
Tento článek popisuje Mezinárodní podpora v knihovně C Runtime.

[Mezinárodní ukázky](https://github.com/Microsoft/VCSamples)<br/>
Obsahuje odkazy na ukázky internacionalizaci v jazyce Visual C++.

[Jazyka a země/Region Strings](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
Poskytuje řetězců jazyka a země/oblast v knihovny run-time jazyka C.