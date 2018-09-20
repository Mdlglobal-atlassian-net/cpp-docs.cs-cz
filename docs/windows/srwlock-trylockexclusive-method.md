---
title: Srwlock::trylockexclusive – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0deec4790d185a5c6b7a7bdcbd670b056fc6f03
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424102"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive – metoda

Pokusí se získat **srwlock –** objektu ve výhradním režimu pro aktuální nebo zadané **SRWLock** objektu. Pokud je volání úspěšné, volající vlákno převezme vlastnictví zámku.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parametry

*lock*<br/>
Ukazatel **SRWLock** objektu.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu, **SRWLock** objektu ve výhradním režimu a volající vlákno převezme vlastnictví zámku. V opačném případě **SRWLock** objekt, jehož stav je neplatný.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[SRWLock – třída](../windows/srwlock-class.md)