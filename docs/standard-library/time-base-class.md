---
title: time_base – třída
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: 85565dc0c0ec904551eb8dd981cfacc9a2e1f256
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460042"
---
# <a name="timebase-class"></a>time_base – třída

Třída slouží jako základní třída pro omezující vlastnosti třídy Template time_get a definuje pouze Výčtový typ `dateorder` a několik konstant tohoto typu.

## <a name="syntax"></a>Syntaxe

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {
        no_order,
        dmy,
        mdy,
        ymd,
        ydm
    };
    time_base(size_t _Refs = 0)
    ~time_base();
};
```

## <a name="remarks"></a>Poznámky

Každá konstanta charakterizuje jiný způsob uspořádání komponent data. Konstanty jsou:

- `no_order`neurčuje žádné konkrétní pořadí.

- `dmy`Určuje den objednávky, měsíc a rok, jako 2. prosince 1979.

- `mdy`Určuje měsíc, den a rok v řádu 2. prosince 1979.

- `ymd`Určuje rok, měsíc a den v řádu, jako v 1979/12/2.

- `ydm`Určuje rok, den a měsíc v řádu 1979: 2 prosinec.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
