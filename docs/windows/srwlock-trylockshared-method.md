---
title: Srwlock::trylockshared – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs:
- C++
helpviewer_keywords:
- TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19ff9324f946f48f201678f9c9e7403ba774b2c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892280"
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