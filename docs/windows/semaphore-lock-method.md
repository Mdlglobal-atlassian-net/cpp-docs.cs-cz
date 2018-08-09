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
ms.openlocfilehash: 39f2fe48b1e7a1a7c6b875b988d861d5fb48698a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642143"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock – metoda
Počká, až do aktuálního objektu nebo **semafor** objekt přidružený k je zadaný popisovač do signalizovaného stavu nebo zadaný časový limit uplynul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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