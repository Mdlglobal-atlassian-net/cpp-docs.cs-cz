---
title: Srwlock::trylockexclusive – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 674a7dced019926e6ea07b41641eb42db70c45a0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013477"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive – metoda
Pokusí se získat **srwlock –** objektu ve výhradním režimu pro aktuální nebo zadané **SRWLock** objektu. Pokud je volání úspěšné, volající vlákno převezme vlastnictví zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *lock*  
 Ukazatel **SRWLock** objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu, **SRWLock** objektu ve výhradním režimu a volající vlákno převezme vlastnictví zámku. V opačném případě **SRWLock** objekt, jehož stav je neplatný.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [SRWLock – třída](../windows/srwlock-class.md)