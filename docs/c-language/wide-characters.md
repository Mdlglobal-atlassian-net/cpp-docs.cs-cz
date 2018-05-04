---
title: Široké znaky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf20b58ad9343f1a90f07a7f4c07bccd397a5888
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="wide-characters"></a>Široké znaky
**ANSI 3.1.3.4** hodnota konstanta znaků celé číslo, které obsahuje více než jeden znak nebo široká Znaková konstanta, která obsahuje více než jeden vícebajtových znaků  
  
 Běžná znaková konstanta 'ab' má celočíselnou hodnotu (int)0x6162. Když je více než jeden bajt, dříve číst bajty posunuty vlevo hodnotou **char_bit –** a další bajtů porovná pomocí operátoru bitové operace OR malou **char_bit –** bits. Počet bajtů ve vícebajtové znakové konstantě nemůže překročit hodnotu sizeof(int), která je pro 32bitový cílový kód 4.  
  
 Vícebajtová znaková konstanta je přečtena dle popisu výše a hodnota je převedena na konstantu širokého znaku pomocí funkce modulu runtime `mbtowc`. Není-li výsledek platnou konstantou širokého znaku, je vygenerována chyba. V každém případě je počet bajtů vyšetřených funkcí `mbtowc` omezen na hodnotu `MB_CUR_MAX`.  
  
## <a name="see-also"></a>Viz také  
 [Znaky](../c-language/characters.md)