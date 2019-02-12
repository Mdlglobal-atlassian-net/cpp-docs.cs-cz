---
title: Identifikátory v primárních výrazech
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
ms.openlocfilehash: 053720bcdf635a7e09363712259b558d93a2972c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151452"
---
# <a name="identifiers-in-primary-expressions"></a>Identifikátory v primárních výrazech

Identifikátory mohou mít celočíselný typ, **float**, `enum`, `struct`, **sjednocení**, pole, ukazatel nebo typ funkce. Identifikátor je primární výraz za předpokladu, že byl deklarován jako označující objekt (v tomto případě je to l hodnota) nebo jako funkce (v tomto případě je to označení funkce). Zobrazit [výrazy L-Value a R-Value](../c-language/l-value-and-r-value-expressions.md) definici l hodnotou.

Hodnota ukazatele, která je představována identifikátorem pole, není proměnná a pole identifikátoru tedy nemůže vytvořit levý operand operátoru přiřazení a nejedná se tedy o upravitelnou l-hodnotu.

Identifikátor deklarovaný jako funkce představuje ukazatel, jehož hodnotou je adresa funkce. Ukazatel adresuje funkci vracející hodnotu zadaného typu. V operacích přiřazení tedy nemohou být l-hodnotami ani identifikátory funkce. Další informace najdete v tématu [identifikátory](../c-language/c-identifiers.md).

## <a name="see-also"></a>Viz také:

[Primární výrazy jazyka C](../c-language/c-primary-expressions.md)
