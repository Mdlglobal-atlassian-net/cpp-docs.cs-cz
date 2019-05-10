---
title: operátor&lt;= (&lt;ukázkový kontejner&gt;)
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
ms.openlocfilehash: 78d49f82f39bc0e96f88ffdcad2cde8a20b0f123
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221379"
---
# <a name="operatorlt-ltsample-containergt"></a>operátor&lt;= (&lt;ukázkový kontejner&gt;)

> [!NOTE]
> Toto téma je v Microsoft C++ dokumentaci jako funkční příklad kontejnerů používané C++ standardní knihovny. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Přetížení **operator < =** k porovnání dvou objektů třídy šablony [kontejneru](../standard-library/sample-container-class.md).

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

[\<Ukázkový kontejner >](../standard-library/sample-container.md)<br/>
