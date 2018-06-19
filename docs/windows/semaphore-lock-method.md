---
title: Semaphore::Lock – metoda | Microsoft Docs
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
ms.openlocfilehash: 80b4db212236da6c9fb320ff5a5e04f4e9f4a4c6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892472"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock – metoda
Počká, dokud nebude aktuální objekt nebo objekt semafor přidružené k zadanému popisovači, je ve stavu signalizovaného nebo zadaný časový limit uplynul.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `milliseconds`  
 Interval časového limitu v milisekundách. Výchozí hodnota je NEKONEČNO, který čeká neomezenou dobu zaseknout.  
  
 `h`  
 Popisovač pro objekt semafor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Details::SyncLockWithStatusT\<HandleTraits::SemaphoreTraits >  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
[Semaphore – třída](../windows/semaphore-class.md)
 