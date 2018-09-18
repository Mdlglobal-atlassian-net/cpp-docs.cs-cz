---
title: Zadejte Conversions (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 606ff0197f73a697aa3dad3bea779de80b060705
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020833"
---
# <a name="type-conversions-c"></a>Převody typu (C)

Převody typu závisí na zadaném operátoru a typu operandu nebo operátorů. Převody typu jsou prováděny v následujících případech:

- pokud je hodnota jednoho typu přiřazena proměnné jiného typu nebo pokud operátor převede typ operandu či operandů před provedením operace,

- pokud je hodnota jednoho typu explicitně přetypována na jiný typ,

- pokud je hodnota předána jako argument funkci nebo pokud je navrácen typ z funkce.

Znak, short integer nebo celočíselné bitové pole, které mají nebo nemají znaménko, případně objekt typu výčtu lze použít ve výrazu všude tam, kde lze použít celé číslo. Pokud může `int` představovat všechny hodnoty původního typu, pak je hodnota převedena na `int`, jinak je převedena na `unsigned int`. Tento proces se nazývá „integrální povýšení“. Integrální povýšení zachovává hodnotu. To znamená, že hodnota po povýšení zůstane stejná jako před povýšením. Zobrazit [obvyklé aritmetické převody](../c-language/usual-arithmetic-conversions.md) Další informace.

## <a name="see-also"></a>Viz také

[Výrazy a přiřazení](../c-language/expressions-and-assignments.md)