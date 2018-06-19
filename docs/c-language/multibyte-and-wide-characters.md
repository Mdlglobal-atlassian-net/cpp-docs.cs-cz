---
title: Vícebajtové a široké znaky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc259a75ab12352a7d0029241496aea22803152a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384197"
---
# <a name="multibyte-and-wide-characters"></a>Vícebajtové a široké znaky
Vícebajtový znak je znak složený ze sekvencí jednoho nebo více bajtů. Každá sekvence bajtů představuje jeden znak rozšířené sady znaků. Vícebajtové znaky se používají v sadách znaků jako Kanji.  
  
 Široké znaky jsou vícejazykové kódy znaků, které jsou vždy 16 bitů široké. Typem znakové konstanty je `char`. Široké znaky jsou typu `wchar_t`. Protože mají široké znaky vždy pevnou velikost, zjednodušuje použití širokých znaků programování mezinárodních znakových sad.  
  
 Řetězcový literál s širokými znaky `L"hello"` se stává polem o šesti celých číslech typu `wchar_t`.  
  
```  
{L'h', L'e', L'l', L'l', L'o', 0}  
```  
  
 Specifikací pro široké znaky je specifikace Unicode. Mezi rutiny knihovny runtime pro převod mezi vícebajtovými a širokými znaky patří rutiny `mbstowcs`, `mbtowc`, `wcstombs` a `wctomb`.  
  
## <a name="see-also"></a>Viz také  
 [Identifikátory jazyka C](../c-language/c-identifiers.md)