---
title: operator = = (&lt;ukázka&gt;kontejneru)
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
ms.openlocfilehash: 08adfcc770551d3050daa46c870b950e468c95b3
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150639"
---
# <a name="operator-ltsample-containergt"></a>operator = = (&lt;ukázka&gt;kontejneru)

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

Přetížení `operator==` k porovnání dvou objektů [kontejneru](../standard-library/sample-container-class.md)šablon tříd.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `left.`ou [velikost](../standard-library/container-class-size.md) `== right.size && equal(left.`[zahajte](../standard-library/container-class-begin.md)`, left.`[End](../standard-library/container-class-end.md)`, right.begin)`.

## <a name="see-also"></a>Viz také

[\<ukázkový kontejner >](../standard-library/sample-container.md)
