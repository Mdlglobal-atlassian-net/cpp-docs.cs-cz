---
title: Srwlockexclusivetraits::Unlock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 7fd6b0fb-8b88-4a43-aa74-0d7fe47a0da6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f30c2d10bd5a25a8241bc52913d675b98e23d88a
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013096"
---
# <a name="srwlockexclusivetraitsunlock-method"></a>SRWLockExclusiveTraits::Unlock – metoda
Uvolní výhradní kontrolu zadaného `SRWLock` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static void Unlock(  
   _In_ Type srwlock  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *srwlock*  
 Popisovač `SRWLock` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [SRWLockExclusiveTraits – struktura](../windows/srwlockexclusivetraits-structure.md)