---
title: Typy znaků
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: f894114d4e980b11edf55c4d4b7c4e60af396fb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312632"
---
# <a name="character-types"></a>Typy znaků

Celočíselná znaková konstanta, která nepředchází písmeno **L** , má `int`typ. Hodnota celočíselné znakové konstanty obsahující jeden znak je číselnou hodnotou znaku, který je interpretován jako celé číslo. Například číselná hodnota znaku `a` je 97 v desítkové soustavě a 61 v šestnáctkové soustavě.

Syntakticky, "konstanta" s "velkým znakem" je znaková konstanta, která je uvozena písmenem **L**. Konstanta s velkým znakem je `wchar_t`typu, celočíselný typ definovaný v STDDEF. Soubor hlaviček H Příklad:

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

Konstanty širokého znaku jsou široké 16 bitů a určují členy znakové sady rozšířeného spuštění. Umožňují vyjádřit znaky abecedy, které jsou příliš velké a nelze je reprezentovat podle typu `char`. Další informace o velkých znacích naleznete v tématu [vícebajtové a velké znaky](../c-language/multibyte-and-wide-characters.md) .

## <a name="see-also"></a>Viz také

[Konstanty znaků jazyka C](../c-language/c-character-constants.md)
