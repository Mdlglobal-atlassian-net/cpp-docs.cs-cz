---
title: Synclockt::synclockt – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3dfee1d923536f519917a50ed44fd5c115007c27
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601964"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT – konstruktor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);
```

### <a name="parameters"></a>Parametry

*Ostatní*  
Odkaz rvalue na jiný **SyncLockT** objektu.

*sync*  
Odkaz na jiný `SyncLockWithStatusT` objektu.

## <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy **SyncLockT** třídy.

První konstruktor inicializuje aktuální **synclockt –** objektu z jiného **synclockt –** objekt zadaný parametrem *jiných*a pak zruší platnost Další  **Synclockt –** objektu. Druhý konstruktor není **chráněné**a inicializuje aktuální **SyncLockT** objekt má neplatný stav.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Viz také

[SyncLockT – třída](../windows/synclockt-class.md)