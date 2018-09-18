---
title: Vícebajtové a široké znaky | Dokumentace Microsoftu
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
ms.openlocfilehash: 2522761389a7f97acf4157683f8fce19e94429d8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100524"
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