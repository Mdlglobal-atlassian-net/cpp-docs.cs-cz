---
title: Synclockwithstatust::getStatus – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2cef491aac3350c1692c2f87236f3cbf01dd9b0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612075"
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
DWORD GetStatus() const;
```

## <a name="return-value"></a>Návratová hodnota

Výsledek operace čekání na objekt, který je založen na **synclockwithstatust –** třídy, jako například [Mutex](../windows/mutex-class1.md) nebo [semafor](../windows/semaphore-class.md). Nula (0) označuje, že operace čekání vrátí signalizovaného stavu; v opačném případě jiný stav došlo k chybě, jako hodnotu časového limitu vypršel.

## <a name="remarks"></a>Poznámky

Načte aktuální stav Čekání **synclockwithstatust –** objektu.

Načte hodnotu základní funkce GetStatus() [status_ –](../windows/synclockwithstatust-status-data-member.md) datový člen. Když se objekt na platformě **synclockwithstatust –** třída provádí operace uzamčení, objekt nejprve počká na objekt k dispozici. Výsledek této operace čekání je uložen v `status_` datový člen. Možné hodnoty `status_` datový člen jsou vrácené hodnoty operace čekání. Další informace najdete v tématu vrácené hodnoty `WaitForSingleObjectEx()` funkce v knihovně MSDN.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Viz také

[SyncLockWithStatusT – třída](../windows/synclockwithstatust-class.md)