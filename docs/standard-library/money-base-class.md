---
title: money_base – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3195d2c988abcfb2d62acb4ece957c8c5156bbd7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965685"
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
