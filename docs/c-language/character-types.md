---
title: Znak typů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c62633d8c7532f15d725018d80f045cf3a37838
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080997"
---
# <a name="character-types"></a>Typy znaků

Celočíselné znakové konstanty nepředchází písmeno **L** má typ `int`. Hodnota celočíselné znakové konstanty obsahující jeden znak je číselnou hodnotou znaku, který je interpretován jako celé číslo. Například číselná hodnota znaku `a` je 97 v desítkové soustavě a 61 v šestnáctkové soustavě.

Syntakticky je "konstanta širokého znaku" Znaková konstanta předchází písmeno **L**. Konstanta širokého znaku je typu `wchar_t`, což je celočíselný typ definovaný v souboru hlaviček STDDEF.H. Příklad:

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

Konstanty širokého znaku jsou široké 16 bitů a určují členy znakové sady rozšířeného spuštění. Umožňují vyjádřit znaky abecedy, které jsou příliš velké a nelze je reprezentovat podle typu `char`. Zobrazit [vícebajtové a široké znaky](../c-language/multibyte-and-wide-characters.md) Další informace o širokých znacích.

## <a name="see-also"></a>Viz také

[Konstanty znaků jazyka C](../c-language/c-character-constants.md)