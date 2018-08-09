---
title: Srwlocksharedtraits::Unlock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 33cdead9-1900-4094-b18e-38fcf1a0bd28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0a42d1e1010f63436951beeadbd833e2a9d445d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650521"
---
# <a name="srwlocksharedtraitsunlock-method"></a>SRWLockSharedTraits::Unlock – metoda
Uvolní výhradní kontrolu zadaného `SRWLock` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline static void Unlock(  
   _In_ Type srwlock  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *srwlock*  
 Popisovač `SRWLock` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [SRWLockSharedTraits – struktura](../windows/srwlocksharedtraits-structure.md)