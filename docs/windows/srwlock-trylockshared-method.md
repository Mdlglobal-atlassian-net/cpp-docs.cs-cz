---
title: Srwlock::trylockshared – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: e67ecd6d5b4968af94ff1a82ad8be24e5b816298
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014244"
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared – metoda
Pokusí se získat **srwlock –** objektu ve sdíleném režimu pro aktuální nebo zadané **SRWLock** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *lock*  
 Ukazatel **SRWLock** objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu, **SRWLock** objektu ve sdíleném režimu a volající vlákno převezme vlastnictví zámku. V opačném případě **SRWLock** objekt, jehož stav je neplatný.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [SRWLock – třída](../windows/srwlock-class.md)