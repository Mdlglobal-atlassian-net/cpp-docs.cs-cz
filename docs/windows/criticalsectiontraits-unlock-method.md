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
ms.openlocfilehash: 2f66f185692c200ea459b88363143c0cc1af9d55
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466007"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock – metoda
Specializuje criticalsection – šablony tak, aby podporoval uvolňující vlastnictví objektu zadaného kritický oddíl.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *cs*  
 Ukazatel na objekt kritický oddíl.  
  
## <a name="remarks"></a>Poznámky  
 *Typ* Modifikátor je definován jako `typedef CRITICAL_SECTION* Type;`.  
  
 Další informace najdete v tématu "LeaveCriticalSection funkce" v části "Synchronizace funkce" dokumentaci k rozhraní Windows API.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [CriticalSectionTraits – struktura](../windows/criticalsectiontraits-structure.md)