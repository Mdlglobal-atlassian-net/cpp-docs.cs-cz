---
title: Srwlocksharedtraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db9a16671be21b2df7a4ce4f9d87a8b66e097e33
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020145"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits – struktura
Popisuje běžné vlastnosti `SRWLock` třídy ve sdíleném režimu zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct SRWLockSharedTraits;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`Type`|Synonymum pro ukazatel [SRWLOCK](../windows/srwlock-class.md) třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SRWLockSharedTraits::GetInvalidValue – metoda](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|Načte **srwlocksharedtraits –** objekt, který je pořád platný.|  
|[SRWLockSharedTraits::Unlock – metoda](../windows/srwlocksharedtraits-unlock-method.md)|Uvolní výhradní kontrolu zadaného `SRWLock` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SRWLockSharedTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::HandleTraits – obor názvů](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)