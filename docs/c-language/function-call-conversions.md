---
title: Převody funkce a volání
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: d9f205bbbbac353b57743f8e1211b20fa3d32f05
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152479"
---
# <a name="function-call-conversions"></a>Převody funkce a volání

Typ převodu provedený pro argumenty ve volání funkce závisí na přítomnosti prototypu funkce (dopředná deklarace) s deklarovanými typy argumentů volané funkce.

Pokud prototyp funkce je k dispozici a zahrnuje deklarované typy argumentů, kompilátor provede kontrolu typů (viz [funkce](../c-language/functions-c.md)).

Pokud žádný prototyp funkce přítomen není, jsou pro argumenty volání funkce provedeny pouze běžné aritmetické převody. Tyto převody jsou provedeny nezávisle na všech argumentech ve volání. To znamená, že **float** hodnota je převedena na **double**; `char` nebo **krátký** hodnota je převedena na `int`; a `unsigned char` nebo **unsigned short** se převede na `unsigned int`.

## <a name="see-also"></a>Viz také:

[Převody typu](../c-language/type-conversions-c.md)
