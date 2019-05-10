---
title: operator!=
ms.date: 11/04/2016
f1_keywords:
- std::!=
- '!='
- std::operator!=
- std.operator!=
- std.!=
- operator!=
helpviewer_keywords:
- '!= operator'
- operator!=
- operator !=
ms.assetid: ef2be7f0-1c94-4edc-b65c-731fddd519f4
ms.openlocfilehash: e29088b64b46e3aa907f4a09ec131c6f9b68a74b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220511"
---
# <a name="operator"></a>operator!=

> [!NOTE]
> Toto téma je v Microsoft C++ dokumentaci jako funkční příklad kontejnerů používané C++ standardní knihovny. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Přetížení `operator!=` k porovnání dvou objektů třídy šablony [kontejneru](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator!=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `!(left == right)`.

## <a name="see-also"></a>Viz také:

[\<Ukázkový kontejner >](../standard-library/sample-container.md)<br/>
