---
title: money_base – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: b0c77b523dbe31bc5b07ae3d736441880fe04546
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383565"
---
# <a name="moneybase-class"></a>money_base – třída

Tato třída popisuje výčet a strukturu společné pro všechny specializace šablony třídy [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Poznámky

Výčet `part` popisuje možné hodnoty prvků pole ve struktuře vzoru. Hodnoty `part` jsou:

- `none` pro vyhledání nula nebo více mezer, nebo generovat žádnou akci.

- `sign` pro vyhledání nebo generovat kladného či záporného znaménka.

- `space` pro vyhledání nula nebo více mezer, nebo vytvořit mezeru.

- `symbol` pro vyhledání nebo generovat symbol měny.

- `value` pro vyhledání nebo generování peněžní hodnoty.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
