---
title: Znak typy | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a48382f5f7a3ab64518c44ec953005cd54a4fe03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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