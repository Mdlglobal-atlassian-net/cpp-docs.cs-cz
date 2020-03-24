---
title: operátor&lt; (&lt;ukázkového kontejneru&gt;)
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
ms.openlocfilehash: 6ef43fb762c4da71062fc846048f21c0112bfafc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215264"
---
# <a name="operatorlt-ltsample-containergt"></a>operátor&lt; (&lt;ukázkového kontejneru&gt;)

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

**Operátor přetížení <** pro porovnání dvou objektů [kontejneru](../standard-library/sample-container-class.md)šablon třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator<(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrací objekt `lexicographical_compare(left.begin, left.end, right.begin, right.end)`.

## <a name="see-also"></a>Viz také

[\<ukázkový kontejner >](../standard-library/sample-container.md)\
[začít](../standard-library/container-class-begin.md)\
[účelu](../standard-library/container-class-end.md)
