---
title: Criticalsectiontraits::Unlock – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b64f44e2188848a25e607c53171e25aa721e9bc4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641363"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock – metoda
Se specializuje `CriticalSection` šablony tak, že podporuje uvolňující vlastnictví objektu zadaného kritický oddíl.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *cs*  
 Ukazatel na objekt kritický oddíl.  
  
## <a name="remarks"></a>Poznámky  
 `Type` Modifikátor je definován jako `typedef CRITICAL_SECTION* Type;`.  
  
 Další informace najdete v tématu **LeaveCriticalSection funkce** v **funkce synchronizace** část dokumentace k rozhraní API Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [CriticalSectionTraits – struktura](../windows/criticalsectiontraits-structure.md)