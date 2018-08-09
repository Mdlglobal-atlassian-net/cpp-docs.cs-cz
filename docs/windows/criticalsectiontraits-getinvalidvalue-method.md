---
title: Criticalsectiontraits::getinvalidvalue – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 01efd9bf3941a5b19e1f0fe6c106d47f1b6e9fcf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642058"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue – metoda
Se specializuje **CriticalSection** šablony tak, aby šablona vždy je neplatná.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí ukazatel na neplatný kritický oddíl.  
  
## <a name="remarks"></a>Poznámky  
 `Type` Modifikátor je definován jako `typedef CRITICAL_SECTION* Type;`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [CriticalSectionTraits – struktura](../windows/criticalsectiontraits-structure.md)