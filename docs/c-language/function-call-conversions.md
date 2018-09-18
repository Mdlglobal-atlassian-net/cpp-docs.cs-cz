---
title: Převody s voláním funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: c3a1a245511f0ab849c28ab9a03ba76903609643
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065657"
---
# <a name="function-call-conversions"></a>Převody funkce a volání

Typ převodu provedený pro argumenty ve volání funkce závisí na přítomnosti prototypu funkce (dopředná deklarace) s deklarovanými typy argumentů volané funkce.

Pokud prototyp funkce je k dispozici a zahrnuje deklarované typy argumentů, kompilátor provede kontrolu typů (viz [funkce](../c-language/functions-c.md)).

Pokud žádný prototyp funkce přítomen není, jsou pro argumenty volání funkce provedeny pouze běžné aritmetické převody. Tyto převody jsou provedeny nezávisle na všech argumentech ve volání. To znamená, že **float** hodnota je převedena na **double**; `char` nebo **krátký** hodnota je převedena na `int`; a `unsigned char` nebo **unsigned short** se převede na `unsigned int`.

## <a name="see-also"></a>Viz také

[Převody typu](../c-language/type-conversions-c.md)