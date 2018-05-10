---
title: money_base – třída | Microsoft Docs
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
ms.openlocfilehash: 805045e4ea63f153e9a35b0d4b068bd69874b93f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="moneybase-class"></a>money_base – třída

Třída popisuje výčet a strukturou společné pro všechny specializací třídy šablony [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Poznámky

Výčet **část** popisuje možné hodnoty v elementech pole pole ve struktuře vzoru. Hodnoty **část** jsou:

- **žádný** odpovídat počtu nula či více mezery nebo nic vygenerování.

- **přihlašovací** odpovídat nebo vygenerování znaménkem kladné a záporné.

- **místo** odpovídat počtu nula či více mezery nebo vygenerování mezerou.

- **symbol** odpovídat nebo vygenerování symbolu měny.

- **Hodnota** odpovídat nebo vygenerování peněžní hodnota.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
