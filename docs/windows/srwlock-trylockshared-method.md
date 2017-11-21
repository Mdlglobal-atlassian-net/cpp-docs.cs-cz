---
title: "Srwlock::trylockshared – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs: C++
helpviewer_keywords: TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 375e4f583531ad1e4eb16b29307445f04d982aea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared – metoda
Pokusí se získat objekt SRWLock ve sdíleném režimu pro objekt SRWLock zadané nebo aktuální.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lock`  
 Ukazatel na objekt SRWLock.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného objekt SRWLock v režimu sdílení a volající vlákno trvá vlastnictví zámku. SRWLock, jinak hodnota objektu, jejichž stav je neplatný.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [SRWLock – třída](../windows/srwlock-class.md)