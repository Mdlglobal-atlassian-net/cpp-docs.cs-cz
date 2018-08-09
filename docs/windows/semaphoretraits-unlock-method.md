---
title: Semaphoretraits::Unlock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98e210ad99a333b6abf68f574916d4f9da5ab67e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650424"
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock – metoda
Ovládací prvek verze sdíleného prostředku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Popisovač **semafor** objektu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud neúspěšná, operace odemknutí **Unlock()** generuje chybu, která určuje příčinu selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [SemaphoreTraits – struktura](../windows/semaphoretraits-structure.md)