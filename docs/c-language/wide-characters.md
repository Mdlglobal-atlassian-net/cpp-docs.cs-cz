---
title: "Široké znaky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab885d5d807fe81b3058d533a70cdbaa9e3e523a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="wide-characters"></a>Široké znaky
**ANSI 3.1.3.4** hodnota konstanta znaků celé číslo, které obsahuje více než jeden znak nebo široká Znaková konstanta, která obsahuje více než jeden vícebajtových znaků  
  
 Běžná znaková konstanta 'ab' má celočíselnou hodnotu (int)0x6162. Když je více než jeden bajt, dříve číst bajty posunuty vlevo hodnotou **char_bit –** a další bajtů porovná pomocí operátoru bitové operace OR malou **char_bit –** bits. Počet bajtů ve vícebajtové znakové konstantě nemůže překročit hodnotu sizeof(int), která je pro 32bitový cílový kód 4.  
  
 Vícebajtová znaková konstanta je přečtena dle popisu výše a hodnota je převedena na konstantu širokého znaku pomocí funkce modulu runtime `mbtowc`. Není-li výsledek platnou konstantou širokého znaku, je vygenerována chyba. V každém případě je počet bajtů vyšetřených funkcí `mbtowc` omezen na hodnotu `MB_CUR_MAX`.  
  
## <a name="see-also"></a>Viz také  
 [Znaky](../c-language/characters.md)