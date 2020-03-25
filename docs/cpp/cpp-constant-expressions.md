---
title: Výrazy konstant v jazyce C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: d4d9803c7f80caba3c33d011e4df433491b9b591
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170576"
---
# <a name="c-constant-expressions"></a>Výrazy konstant v jazyce C++

*Konstantní* hodnota je jedna, která se nemění. C++poskytuje dvě klíčová slova, která umožňují vyjádřit záměr, že objekt není určen pro úpravu, a k vykonání tohoto záměru.

C++vyžaduje konstantní výrazy – výrazy, které se vyhodnotí na konstantu – pro deklarace:

- Hranice pole

- Selektory v příkazech Case

- Specifikace délky bitového pole

- Inicializátory výčtu

Jedinými operandy, které jsou platné v konstantních výrazech, jsou:

- Literály

- Konstanty výčtu

- Hodnoty deklarované jako const, které jsou inicializovány pomocí konstantních výrazů

- výrazy **sizeof**

Neintegrální konstanty musí být převedeny (explicitně nebo implicitně) na integrální typy, aby byly platné v konstantním výrazu. Proto je platný následující kód:

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Explicitní převody na integrální typy jsou platné v konstantních výrazech; všechny ostatní typy a odvozené typy jsou neplatné s výjimkou případů, kdy se používají jako operandy operátoru **sizeof** .

Operátor čárky a přiřazení operátory nelze použít v konstantních výrazech.

## <a name="see-also"></a>Viz také

[Typy výrazů](../cpp/types-of-expressions.md)
