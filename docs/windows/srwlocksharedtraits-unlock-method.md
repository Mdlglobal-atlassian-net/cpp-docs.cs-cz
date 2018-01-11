---
title: "Srwlocksharedtraits::Unlock – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs: C++
helpviewer_keywords: Unlock method
ms.assetid: 33cdead9-1900-4094-b18e-38fcf1a0bd28
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: beca240c99dd4e0cacfa0f28024dab10883614b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="srwlocksharedtraitsunlock-method"></a>SRWLockSharedTraits::Unlock – metoda
Uvolní výhradní kontrolu nad zadaný objekt SRWLock.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline static void Unlock(  
   _In_ Type srwlock  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `srwlock`  
 Popisovač pro objekt SRWLock.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [SRWLockSharedTraits – struktura](../windows/srwlocksharedtraits-structure.md)