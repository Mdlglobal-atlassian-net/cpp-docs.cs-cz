---
title: Znak typy | Microsoft Docs
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
ms.openlocfilehash: 1cd26eea35da463211b144e98faa0636f5204f6f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383690"
---
# <a name="character-types"></a>Typy znaků
Celočíselná konstanta znak není před písmeno **L** má typ `int`. Hodnota celočíselné znakové konstanty obsahující jeden znak je číselnou hodnotou znaku, který je interpretován jako celé číslo. Například číselná hodnota znaku `a` je 97 v desítkové soustavě a 61 v šestnáctkové soustavě.  
  
 Syntakticky, "široká charakterová konstanta" je znak konstanta předponu písmene **L**. Konstanta širokého znaku je typu `wchar_t`, což je celočíselný typ definovaný v souboru hlaviček STDDEF.H. Příklad:  
  
```  
char    schar =  'x';   /* A character constant          */  
wchar_t wchar = L'x';   /* A wide-character constant for   
                            the same character           */  
```  
  
 Konstanty širokého znaku jsou široké 16 bitů a určují členy znakové sady rozšířeného spuštění. Umožňují vyjádřit znaky abecedy, které jsou příliš velké a nelze je reprezentovat podle typu `char`. V tématu [vícebajtové a široké znaky](../c-language/multibyte-and-wide-characters.md) Další informace o širokých znacích.  
  
## <a name="see-also"></a>Viz také  
 [Konstanty znaků jazyka C](../c-language/c-character-constants.md)