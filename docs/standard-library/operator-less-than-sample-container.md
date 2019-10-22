---
title: operátor &lt; (&gt; &lt;sample kontejneru)
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
ms.openlocfilehash: fc2a14d882b5ccfbfdaae543c76ca673f9018a59
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687328"
---
# <a name="operatorlt-ltsample-containergt"></a>operátor &lt; (&gt; &lt;sample kontejneru)

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

Vrátí `lexicographical_compare(left.begin, left.end, right.begin, right.end)`.

## <a name="see-also"></a>Viz také:

[\<sample > kontejneru](../standard-library/sample-container.md) \
[začít](../standard-library/container-class-begin.md) \
[účelu](../standard-library/container-class-end.md)