---
title: Synclockwithstatust::synclockwithstatust – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 020632ff17ade10e7fcb9cd46d245849189b6860
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416783"
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT – konstruktor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Odkaz rvalue na jiný **synclockwithstatust –** objektu.

*sync*<br/>
Odkaz na jiný **synclockwithstatust –** objektu.

*Stav*<br/>
Hodnota [status_ –](../windows/synclockwithstatust-status-data-member.md) datový člen třídy *jiných* parametr nebo *synchronizace* parametr.

## <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy **synclockwithstatust –** třídy.

První konstruktor inicializuje aktuální **synclockwithstatust –** objektu z jiného **synclockwithstatust –** určené parametrem *jiných*a pak zruší platnost druhé **synclockwithstatust –** objektu. Druhý konstruktor není **chráněné**a inicializuje aktuální **synclockwithstatust –** objekt má neplatný stav.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Viz také

[SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)<br/>
[SyncLockWithStatusT::GetStatus – metoda](../windows/synclockwithstatust-getstatus-method.md)