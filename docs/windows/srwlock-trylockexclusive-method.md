---
title: "Srwlock::trylockexclusive – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs: C++
helpviewer_keywords: TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a23629ae5bc7d1645367019ea38d747779b84b16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive – metoda
Pokusí se získat objekt SRWLock ve výhradním režimu pro objekt SRWLock zadané nebo aktuální. Pokud je volání úspěšné, volající vlákno trvá vlastnictví zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lock`  
 Ukazatel na objekt SRWLock.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného objekt SRWLock ve výhradním režimu a volající vlákno trvá vlastnictví zámku. SRWLock, jinak hodnota objektu, jejichž stav je neplatný.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [SRWLock – třída](../windows/srwlock-class.md)