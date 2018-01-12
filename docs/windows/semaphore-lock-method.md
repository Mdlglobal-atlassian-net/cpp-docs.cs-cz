---
title: "Semaphore::Lock – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs: C++
helpviewer_keywords: Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11531a07f161722947d03a53392b8315b7593958
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 