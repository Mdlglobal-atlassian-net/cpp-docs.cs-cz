---
title: Operator == (&lt;ukázkový kontejner&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: c49c58bdc168385d421cf942735b7473de70925f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613496"
---
# <a name="operator-ltsample-containergt"></a>Operator == (&lt;ukázkový kontejner&gt;)

> [!NOTE]
> Toto téma je v dokumentaci k Visual C++ jako funkční příklad kontejnery používané ve standardní knihovně jazyka C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Přetížení `operator==` k porovnání dvou objektů třídy šablony [kontejneru](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `left.` [velikost](../standard-library/container-class-size.md) ` == right.size && equal(left.` [začít](../standard-library/container-class-begin.md)`, left.`[end](../standard-library/container-class-end.md)`, right.begin)`.

## <a name="see-also"></a>Viz také:

[\<Ukázkový kontejner >](../standard-library/sample-container.md)<br/>
