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
ms.openlocfilehash: db246cda79c778f37c5afbfda4a68c191c474e12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190492"
---
# <a name="bool-c"></a>bool (C++)

Toto klíčové slovo je vestavěný typ. Proměnná tohoto typu může mít hodnoty [true](../cpp/true-cpp.md) a [false](../cpp/false-cpp.md). Podmíněné výrazy mají typ **bool** , takže mají hodnoty typu **bool**. Například `i!=0` nyní má hodnotu TRUE nebo FALSE v závislosti na hodnotě `i`.

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): operand přípony nebo příznaku snížení předpony nebo odčítání nesmí být typu **bool**. Jinými slovy, s ohledem na proměnnou `b` typu **bool**, tyto výrazy již nejsou povoleny:

```cpp
    b++;
    ++b;
    b--;
    --b;
```

Hodnoty PRAVDA a NEPRAVDA mají následující vztah:

```cpp
!false == true
!true == false
```

V následujícím příkazu:

```cpp
if (condexpr1) statement1;
```

Pokud má `condexpr1` hodnotu TRUE, `statement1` je vždy spuštěná; Pokud je `condexpr1` FALSE, `statement1` se nikdy nespustí.

Při použití přípony nebo předpony **++** operátoru na proměnnou typu **bool**je proměnná nastavena na hodnotu true.
**Visual Studio 2017 verze 15,3 a novější**: operátor + + pro **bool** byl odebrán z jazyka a již není podporován.

Operátor přípony nebo předpony **--** nelze použít na proměnnou tohoto typu.

Typ **bool** se účastní integrální propagace. R-hodnota typu **bool** může být převedena na hodnotu r typu **int**, přičemž hodnota false se stane nula a true se stane jednou. V případě odlišného typu se **logická** hodnota podílí na řešení přetížení.

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Předdefinované typy](../cpp/fundamental-types-cpp.md)
