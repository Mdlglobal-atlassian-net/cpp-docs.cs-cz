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
ms.openlocfilehash: 27dcdbf810199c62b7c267270ad62ed1ed677494
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503351"
---
# <a name="type-conversions-c"></a>Převody typu (C)

Převody typu závisí na zadaném operátoru a typu operandu nebo operátorů. Převody typu jsou prováděny v následujících případech:

- pokud je hodnota jednoho typu přiřazena proměnné jiného typu nebo pokud operátor převede typ operandu či operandů před provedením operace,

- pokud je hodnota jednoho typu explicitně přetypována na jiný typ,

- pokud je hodnota předána jako argument funkci nebo pokud je navrácen typ z funkce.

Znak, short integer nebo celočíselné bitové pole, které mají nebo nemají znaménko, případně objekt typu výčtu lze použít ve výrazu všude tam, kde lze použít celé číslo. Pokud může `int` představovat všechny hodnoty původního typu, pak je hodnota převedena na `int`, jinak je převedena na `unsigned int`. Tento proces se nazývá „integrální povýšení“. Integrální povýšení zachovává hodnotu. To znamená, že hodnota po povýšení zůstane stejná jako před povýšením. Zobrazit [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) Další informace.

## <a name="see-also"></a>Viz také

[Výrazy a přiřazení](../c-language/expressions-and-assignments.md)