---
title: money_base – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: 5b19635cf4d2cce58ec50226c463a075cfac5b0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455569"
---
# <a name="moneybase-class"></a>money_base – třída

Třída popisuje výčet a strukturu společnou pro všechny specializace třídy template [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Poznámky

Výčet `part` popisuje možné hodnoty v prvcích pole Array ve vzoru struktury. Hodnoty `part` jsou:

- `none`pro vyhledání žádného nebo více mezer nebo vygenerování nic.

- `sign`pro spárování nebo vygenerování kladného nebo záporného znaménka.

- `space`pro vyhledání žádného nebo více mezer nebo vygenerování prostoru.

- `symbol`pro spárování nebo vygenerování symbolu měny.

- `value`pro spárování nebo vygenerování peněžní hodnoty.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
