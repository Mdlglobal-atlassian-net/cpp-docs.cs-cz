---
title: Srwlock::lockshared – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
dev_langs:
- C++
helpviewer_keywords:
- LockShared method
ms.assetid: 9d826a5c-b6a2-4430-ac85-d5753cbca889
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fda64126709515fcf3e174a6f3cbdea22d5ee9e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011059"
---
# <a name="srwlocklockshared-method"></a>SRWLock::LockShared – metoda
Získá **SRWLock** objektu ve sdíleném režimu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SyncLockShared LockShared();  
  
static SyncLockShared LockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *lock*  
 Ukazatel **SRWLock** objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 **SRWLock** objektu ve sdíleném režimu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [SRWLock – třída](../windows/srwlock-class.md)