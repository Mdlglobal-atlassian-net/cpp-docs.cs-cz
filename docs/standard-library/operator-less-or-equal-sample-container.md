---
title: operator &lt; = (&lt;sample kontejneru &gt;)
ms.date: 11/04/2016
f1_keywords:
- std::<=
- std.operator<=
- operator<=
- std.<=
- std::operator<=
- <=
helpviewer_keywords:
- operator<=
- operator <=
- <= operator, with specific objects
- <= operator
ms.assetid: 338577dd-dc88-4a2b-9e12-0379c54fc8a2
ms.openlocfilehash: fff370d595afaf4b4692b4166f248b56a72efcb8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689182"
---
# <a name="operatorlt-ltsample-containergt"></a>operator &lt; = (&lt;sample kontejneru &gt;)

> [!NOTE]
> Toto téma se nachází v dokumentaci C++ společnosti Microsoft jako nefunkční příklad kontejnerů použitých ve C++ standardní knihovně. Další informace najdete v tématu [ C++ standardní kontejnery knihovny](../standard-library/stl-containers.md).

**Operátor přetížení < =** k porovnání dvou objektů [kontejneru](../standard-library/sample-container-class.md)šablon třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator<=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `!(right < left)`.

## <a name="see-also"></a>Viz také:

[> kontejneru \<sample](../standard-library/sample-container.md)
