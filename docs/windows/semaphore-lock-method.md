---
title: Semaphore::Lock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47925bcc647d253775e4dd61f6a7f5d5fb586dde
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599280"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock – metoda

Počká, až do aktuálního objektu nebo **semafor** objekt přidružený k je zadaný popisovač do signalizovaného stavu nebo zadaný časový limit uplynul.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Parametry

*Milisekundy*  
Interval časového limitu v milisekundách. Výchozí hodnota je NEKONEČNO, který čekat po neomezenou dobu.

*h*  
Popisovač **semafor** objektu.

## <a name="return-value"></a>Návratová hodnota

A `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[Semaphore – třída](../windows/semaphore-class.md)