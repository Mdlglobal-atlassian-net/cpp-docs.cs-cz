---
title: Výrazy konstant v jazyce C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 97059066adadc3a7897cbd2c4c747e2a673e7201
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576420"
---
# <a name="c-constant-expressions"></a>Výrazy konstant v jazyce C++

A *konstantní* hodnota je 1, která se nezmění. Jazyk C++ poskytuje dvě klíčová slova, které umožňují vyjádřit záměr, že objekt není určen má být upraven a k vynucení tohoto záměru.

C++ vyžaduje konstantní výrazy – výrazy, které vedou na konstantu – pro deklarace:

- Hranice pole

- Selektory v příkazu case

- Specifikace délky bitového pole

- Inicializátory výčet

Pouze operandy, které jsou platné v konstantních výrazech jsou:

- Literály

- Konstanty výčtu

- Hodnoty deklarované jako jako const, které jsou inicializovány pomocí výrazů konstant

- **operátor sizeof:** výrazy

Nonintegral konstanty musí být převeden (explicitně nebo implicitně) na jeho platnost v konstantním výrazu integrální typy. Proto je platný následující kód:

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Explicitní převody na integrální typy jsou platné v konstantních výrazech; všechny ostatní typy a odvozené typy jsou neplatné s výjimkou při používat jako operandy **sizeof** operátor.

Operátor čárky a operátory přiřazení nelze použít v konstantních výrazech.

## <a name="see-also"></a>Viz také:

[Typy výrazů](../cpp/types-of-expressions.md)