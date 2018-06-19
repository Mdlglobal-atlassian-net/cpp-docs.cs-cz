---
title: time_base – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c13cd76f5d353cf91997406c8e7f74b5383cf8e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854493"
---
# <a name="timebase-class"></a>time_base – třída

Třída slouží jako základní třídu pro omezující vlastnosti time_get – třída šablony, definování právě Výčtový typ **dateorder** a několik konstanty tohoto typu.

## <a name="syntax"></a>Syntaxe

```cpp
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
 ~time_base();

};
```

## <a name="remarks"></a>Poznámky

Každý konstanta charakterizuje jiný způsob, jak pořadí komponenty data. Konstanty jsou:

- **no_order** určuje žádné konkrétní pořadí.

- **DMY** určuje pořadí den, měsíc a pak roku, stejně jako 2 prosince 1979.

- **formát MDR** určuje pořadí měsíc, den, pak roku, stejně jako 2. prosince 1979.

- **RMD** určuje pořadí rok, měsíc a den, stejně jako 1979/12/2.

- **rdm** určuje pořadí roku, den, pak měsíc jako Dec 1979:2.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
