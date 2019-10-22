---
title: money_base – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: c614832b0cbb1cc23e42ecb3a939ccf1334a5cea
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689314"
---
# <a name="money_base-class"></a>money_base – třída

Třída popisuje výčet a strukturu společnou pro všechny specializace šablony třídy [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Poznámky

@No__t_0 výčtu popisuje možné hodnoty v prvcích pole Array ve vzoru struktury. Hodnoty `part` jsou:

- `none` odpovídat žádnému nebo více mezerám nebo generovat nic.

- `sign`, aby odpovídaly nebo vygenerovaly kladné nebo záporné znaménko.

- `space` odpovídat žádnému nebo více mezerám nebo vygenerovat mezeru.

- `symbol`, aby odpovídaly nebo vygenerovaly symbol měny.

- `value`, aby odpovídaly nebo vygenerovaly peněžní hodnotu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
