---
title: operator = = (&lt;ukázkový kontejner&gt;)
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
ms.openlocfilehash: 168785abb09ca198435c301040d7628a6dd12b26
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460159"
---
# <a name="operator-ltsample-containergt"></a>operator = = (&lt;ukázkový kontejner&gt;)

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

Přetížení `operator==` pro porovnání dvou objektů [kontejneru](../standard-library/sample-container-class.md)tříd šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `left.` ` == right.size && equal(left.` [začátek](../standard-library/container-class-begin.md) [](../standard-library/container-class-size.md) tétovelikosti`, right.begin)`[](../standard-library/container-class-end.md).`, left.`

## <a name="see-also"></a>Viz také:

[\<Ukázkový > kontejneru](../standard-library/sample-container.md)
