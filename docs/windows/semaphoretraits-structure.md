---
title: Semaphoretraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
dev_langs:
- C++
helpviewer_keywords:
- SemaphoreTraits structure
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c953efc6e9f4b3904404ae362b6beca7f88192d2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018266"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits – struktura
Definuje běžné vlastnosti **semafor** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct SemaphoreTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SemaphoreTraits::Unlock – metoda](../windows/semaphoretraits-unlock-method.md)|Ovládací prvek verze sdíleného prostředku.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HANDLENullTraits`  
  
 `SemaphoreTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::HandleTraits – obor názvů](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)