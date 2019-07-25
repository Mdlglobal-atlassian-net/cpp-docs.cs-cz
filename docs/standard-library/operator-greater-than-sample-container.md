---
title: –&gt; operátor&lt;(ukázkový&gt;kontejner)
ms.date: 11/04/2016
f1_keywords:
- std::operator>
- operator>
- std::>
- '>'
helpviewer_keywords:
- '> operator, comparing specific objects'
- operator >
ms.assetid: 49bd417a-3305-4ffa-9884-39d3904ed87d
ms.openlocfilehash: e7da0250dc647d2d519b9c3d105fb942717c7a4c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449747"
---
# <a name="operatorgt-ltsample-containergt"></a>–&gt; operátor&lt;(ukázkový&gt;kontejner)

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

**Operátor přetížení >** pro porovnání dvou objektů [kontejneru](../standard-library/sample-container-class.md)tříd šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator*gt;(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `right < left`.

## <a name="see-also"></a>Viz také:

[\<Ukázkový > kontejneru](../standard-library/sample-container.md)
