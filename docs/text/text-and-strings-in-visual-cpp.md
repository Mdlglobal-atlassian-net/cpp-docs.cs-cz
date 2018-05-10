---
title: Text a řetězce v jazyce Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e16c44993f3cd9598bc42f9151264e09ac3b7a53
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="text-and-strings-in-visual-c"></a>Text a řetězce v jazyce Visual C++
Vývoj aplikací pro mezinárodní trhy důležitým aspektem je odpovídající reprezentace místní znakové sady. Znaková sada ASCII definuje znaky v rozsahu od 0x00 do 0x7F. Existují jiné znakové sady, především Evropské, které definovat znaky v rozsahu od 0x00 do 0x7F stejně jako na znakové sadě ASCII a také rozšířenou znakovou sadu z 0x80 do 0xFF. Proto je dostačující k reprezentaci znaková sada ASCII, jakož i znakové sady mnoha evropských jazyků 8bitové, jedním znaková sada (SBCS). Ale některé neevropské znakových sad, jako je například japonské Kanji, zahrnují mnoho více znaků, než schéma kódování jednobajtové představují a proto vyžaduje, že vícebajtové znakové sady (MBCS) kódování.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Unicode a MBCS](../text/unicode-and-mbcs.md)  
 Popisuje podporu Visual C++ pro kódování Unicode a MBCS programování.  
  
 [Podpora pro Unicode](../text/support-for-unicode.md)  
 Popisuje kódování Unicode, specifikace pro podporu všech znakových sad, včetně znakových sad, které nelze vyjádřit v byl jediný bajt.  
  
 [Podpora vícebajtových znakových sad (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)  
 Popisuje MBCS, pro podporu znakových sad, například japonštiny a čínština, který nelze v jednom bajtu alternativu ke kódování Unicode.  
  
 [Mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md)  
 Mapování obecného textu specifické pro společnost Microsoft poskytuje pro mnoho typů dat, rutiny a jiné objekty.  
  
 [Postupy: Převody mezi různými typy řetězců](../text/how-to-convert-between-various-string-types.md)  
 Ukazuje, jak převést různými typy řetězců Visual C++ do jiných řetězců.  
  
## <a name="related-sections"></a>Související oddíly  
 [Internacionalizace](../c-runtime-library/internationalization.md)  
 Popisuje mezinárodní podpora v běhové knihovny jazyka C.  
  
 [Mezinárodní ukázky](http://msdn.microsoft.com/en-us/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 Obsahuje odkazy na internacionalizaci v jazyce Visual C++ – ukázky.  
  
 [Jazyk a řetězce zemí/oblastí](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 Poskytuje řetězce jazyka a země nebo oblast v běhové knihovny jazyka C.