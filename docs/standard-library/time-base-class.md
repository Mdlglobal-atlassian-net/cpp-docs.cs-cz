---
title: time_base – třída
ms.date: 11/04/2016
f1_keywords:
- locale/std::time_base
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
ms.openlocfilehash: e790237e506aa32bafdb39938d841307bbc4d9c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412017"
---
# <a name="timebase-class"></a>time_base – třída

Tato třída slouží jako základní třída pro omezující vlastnosti třídy šablony time_get, definující pouze výčtového typu `dateorder` a několik konstant tohoto typu.

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

Jednotlivých konstantách charakterizuje jiný způsob, jak uspořádat součásti datum. Konstanty jsou:

- `no_order` Určuje bez určitého pořadí.

- `dmy` Určuje pořadí den, měsíc a rok, stejně jako v 2 1979 dne.

- `mdy` Určuje pořadí měsíc, den a rok, stejně jako v 2. prosince 1979.

- `ymd` Určuje pořadí rok, měsíc a den jako 1979/12/2.

- `ydm` Určuje pořadí roku, den a měsíc, stejně jako v 1979: 2 Dec.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
