---
title: Výrazy konstant v jazyce C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35041b3a58f53586702db73d3bc5f6103f4f7cd7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054360"
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