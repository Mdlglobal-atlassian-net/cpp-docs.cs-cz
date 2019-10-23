---
title: time_base – třída
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: ddaf9905e859c062031940d35adfa2a3393dbb5a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685791"
---
# <a name="time_base-class"></a>time_base – třída

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

- `no_order` neurčuje žádné konkrétní pořadí.

- `dmy` Určuje den objednávky, měsíc a rok, jako 2. prosince 1979.

- `mdy` Určuje měsíc, den a rok v řádu 2. prosince 1979.

- `ymd` určuje rok, měsíc a den v řádu 1979/12/2.

- `ydm` určuje rok, den a měsíc, jako v 1979:2 prosinec.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
