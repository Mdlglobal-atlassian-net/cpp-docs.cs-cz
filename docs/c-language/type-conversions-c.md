---
title: Převody typu (C)
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
ms.openlocfilehash: 281234b857a97acbb57ebbfca7b678a637d00764
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147396"
---
# <a name="type-conversions-c"></a>Převody typu (C)

Převody typu závisí na zadaném operátoru a typu operandu nebo operátorů. Převody typu jsou prováděny v následujících případech:

- pokud je hodnota jednoho typu přiřazena proměnné jiného typu nebo pokud operátor převede typ operandu či operandů před provedením operace,

- pokud je hodnota jednoho typu explicitně přetypována na jiný typ,

- pokud je hodnota předána jako argument funkci nebo pokud je navrácen typ z funkce.

Znak, short integer nebo celočíselné bitové pole, které mají nebo nemají znaménko, případně objekt typu výčtu lze použít ve výrazu všude tam, kde lze použít celé číslo. Pokud může `int` představovat všechny hodnoty původního typu, pak je hodnota převedena na `int`, jinak je převedena na `unsigned int`. Tento proces se nazývá „integrální povýšení“. Integrální povýšení zachovává hodnotu. To znamená, že hodnota po povýšení zůstane stejná jako před povýšením. Zobrazit [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) Další informace.

## <a name="see-also"></a>Viz také:

[Výrazy a přiřazení](../c-language/expressions-and-assignments.md)
