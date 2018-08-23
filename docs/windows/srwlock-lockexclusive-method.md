---
title: Srwlock::lockexclusive – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
dev_langs:
- C++
helpviewer_keywords:
- LockExclusive method
ms.assetid: f361b672-fca6-45cc-a9b4-310cc0d23fdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6218bfe1bbdc27749bed1395108b7a30533c50b7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596880"
---
# <a name="srwlocklockexclusive-method"></a>SRWLock::LockExclusive – metoda

Získá **SRWLock** objektu ve výhradním režimu.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*  
Ukazatel **SRWLock** objektu.

## <a name="return-value"></a>Návratová hodnota

**SRWLock** objektu ve výhradním režimu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[SRWLock – třída](../windows/srwlock-class.md)