---
title: Srwlocksharedtraits::Unlock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 33cdead9-1900-4094-b18e-38fcf1a0bd28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e00b898fc60953896a9c0d2b7a124e195d3bcbf1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593165"
---
# <a name="srwlocksharedtraitsunlock-method"></a>SRWLockSharedTraits::Unlock – metoda

Uvolní výhradní kontrolu zadaného `SRWLock` objektu.

## <a name="syntax"></a>Syntaxe

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parametry

*srwlock*  
Popisovač `SRWLock` objektu.

## <a name="return-value"></a>Návratová hodnota

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Viz také

[SRWLockSharedTraits – struktura](../windows/srwlocksharedtraits-structure.md)