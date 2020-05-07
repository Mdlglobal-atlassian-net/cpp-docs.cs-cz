---
title: Převody funkce a volání
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: d9f205bbbbac353b57743f8e1211b20fa3d32f05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233215"
---
# <a name="function-call-conversions"></a>Převody funkce a volání

Typ převodu provedený pro argumenty ve volání funkce závisí na přítomnosti prototypu funkce (dopředná deklarace) s deklarovanými typy argumentů volané funkce.

Pokud prototyp funkce je přítomen a obsahuje deklarované typy argumentů, kompilátor provede kontrolu typu (viz [funkce](../c-language/functions-c.md)).

Pokud žádný prototyp funkce přítomen není, jsou pro argumenty volání funkce provedeny pouze běžné aritmetické převody. Tyto převody jsou provedeny nezávisle na všech argumentech ve volání. To znamená, že hodnota **typu float** je převedena na **typ Double**; `char` nebo **krátká** hodnota je převedena na `int`. a `unsigned char` **krátká znaménka nebo nebo bez znaménka** jsou převedena na `unsigned int`.

## <a name="see-also"></a>Viz také

[Převody typu](../c-language/type-conversions-c.md)
