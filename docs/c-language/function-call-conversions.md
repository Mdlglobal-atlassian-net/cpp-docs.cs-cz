---
title: "Převody funkce a volání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f45a7b3b4aecfd25d1973e1e95ec787e958025e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="function-call-conversions"></a>Převody funkce a volání
Typ převodu provedený pro argumenty ve volání funkce závisí na přítomnosti prototypu funkce (dopředná deklarace) s deklarovanými typy argumentů volané funkce.  
  
 Pokud prototyp funkce je k dispozici a obsahuje typy deklarované argumentů, kompilátor provede kontrola typu (viz [funkce](../c-language/functions-c.md)).  
  
 Pokud žádný prototyp funkce přítomen není, jsou pro argumenty volání funkce provedeny pouze běžné aritmetické převody. Tyto převody jsou provedeny nezávisle na všech argumentech ve volání. To znamená, že **float** je převést hodnotu **dvojité**; `char` nebo **krátký** hodnota je převedena na `int`; a `unsigned char` nebo **nepodepsané prostě** jsou převedeny na `unsigned int`.  
  
## <a name="see-also"></a>Viz také  
 [Převody typu](../c-language/type-conversions-c.md)