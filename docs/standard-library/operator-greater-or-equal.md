---
title: operátor&gt;= | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- operator>=
- std::>=
- std.operator>=
- '>='
- std.>=
- std::operator>=
dev_langs:
- C++
helpviewer_keywords:
- '>= operator, comparing specific objects'
- operator >=
- operator>=
ms.assetid: 14fbebf5-8b75-4afa-a51b-3112d31c07cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 958d87b0c9eb07c3d5c0fea5f2ff06f7b12aee75
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855809"
---
# <a name="operatorgt"></a>Operátor&gt;=

> [!NOTE]
> Toto téma se v dokumentaci k Visual C++ jako funkční příklad kontejnery použít ve standardní knihovně C++. Další informace najdete v tématu [kontejnery standardní knihovny C++](../standard-library/stl-containers.md).

Přetížení **operator > =** k porovnání dvou objektů třídy šablony [kontejneru](../standard-library/sample-container-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
bool operator>=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí `!(left < right)`.

## <a name="see-also"></a>Viz také

[\<Ukázkový kontejner >](../standard-library/sample-container.md)<br/>
