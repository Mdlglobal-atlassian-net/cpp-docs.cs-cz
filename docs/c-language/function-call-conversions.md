---
title: Převody funkce a volání | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71b0fc4468ea98f04c87c8389021f2e12d9cae69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384493"
---
# <a name="function-call-conversions"></a>Převody funkce a volání
Typ převodu provedený pro argumenty ve volání funkce závisí na přítomnosti prototypu funkce (dopředná deklarace) s deklarovanými typy argumentů volané funkce.  
  
 Pokud prototyp funkce je k dispozici a obsahuje typy deklarované argumentů, kompilátor provede kontrola typu (viz [funkce](../c-language/functions-c.md)).  
  
 Pokud žádný prototyp funkce přítomen není, jsou pro argumenty volání funkce provedeny pouze běžné aritmetické převody. Tyto převody jsou provedeny nezávisle na všech argumentech ve volání. To znamená, že **float** je převést hodnotu **dvojité**; `char` nebo **krátký** hodnota je převedena na `int`; a `unsigned char` nebo **nepodepsané prostě** jsou převedeny na `unsigned int`.  
  
## <a name="see-also"></a>Viz také  
 [Převody typu](../c-language/type-conversions-c.md)