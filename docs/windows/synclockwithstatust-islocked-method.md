---
title: Synclockwithstatust::islocked – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d70a2c316f9e7994292f3dc29cef5bce993778ad
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595060"
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
bool IsLocked() const;
```

## <a name="remarks"></a>Poznámky

Označuje, zda aktuální **synclockwithstatust –** vlastní prostředek objektu; to znamená, **synclockwithstatust –** objekt je *uzamčen*.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud **synclockwithstatust –** objekt je uzamčena, jinak **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Viz také

[SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)