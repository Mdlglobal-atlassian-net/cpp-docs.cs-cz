---
title: –&lt; operátor&lt;(ukázkový&gt;kontejner)
ms.date: 11/04/2016
f1_keywords:
- std::operator<
- operator<
- std.<
- <
- std.operator<
- std::<
helpviewer_keywords:
- < operator, comparing specific objects
- operator<, valarrays
- < operator
- operator <, valarrays
ms.assetid: 31027dd6-53be-428b-b950-1dcb25393597
ms.openlocfilehash: a286833d96e913a66240d25798e1cc230adf58b0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458729"
---
# <a name="operatorlt-ltsample-containergt"></a>–&lt; operátor&lt;(ukázkový&gt;kontejner)

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

**Operátor přetížení <** pro porovnání dvou objektů [kontejneru](../standard-library/sample-container-class.md)tříd šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `lexicographical_compare(left.begin, left.end, right.begin, right.end)`.

## <a name="see-also"></a>Viz také:

[\<Ukázkový > kontejneru](../standard-library/sample-container.md)\
[ifunctiondiscovery](../standard-library/container-class-begin.md)\
[účelu](../standard-library/container-class-end.md)