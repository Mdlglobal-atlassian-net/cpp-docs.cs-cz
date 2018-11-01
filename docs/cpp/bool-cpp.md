---
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: e481cb9de7c80d147179efceab2fda9b160f3c21
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638123"
---
# <a name="bool-c"></a>bool (C++)

Toto klíčové slovo je vestavěný typ. Proměnná tohoto typu může mít hodnoty [true](../cpp/true-cpp.md) a [false](../cpp/false-cpp.md). Podmíněné výrazy jsou typu **bool** a mají proto hodnoty typu **bool**. Například `i!=0` teď má hodnotu TRUE nebo FALSE, v závislosti na hodnotě z `i`.

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): operand uplatněna přípona nebo předpona Inkrementace nebo dekrementace operátor nesmí být typu **bool**. Jinými slovy, zadané proměnné `b` typu **bool**, už nejsou povolené tyto výrazy:

```cpp
    b++;
    ++b;
    b--;
    --b;
```

Hodnoty TRUE a FALSE mají následující vztah:

```cpp
!false == true
!true == false
```

V následujícím příkazu:

```cpp
if (condexpr1) statement1;
```

Pokud `condexpr1` má hodnotu TRUE, `statement1` je vždy spuštěn; pokud `condexpr1` má hodnotu FALSE, `statement1` není nikdy proveden.

Uplatněna přípona nebo předpona **++** operátor je použít pro proměnné typu **bool**, proměnná je nastavena na hodnotu TRUE.
**Visual Studio 2017 verze 15.3 nebo novější**: operator ++ pro **bool** byl odebrán z jazyka a už není podporovaná.

Přípony nebo předpony **--** operátor nelze použít na proměnné tohoto typu.

**Bool** typ se účastní integrální propagace. R-value typu **bool** lze převést na hodnotu r-value typu **int**, se stávají FALSE nula a TRUE jedna. Jako odlišný typ se **bool** účastní řešení přetížení.

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Základní typy](../cpp/fundamental-types-cpp.md)