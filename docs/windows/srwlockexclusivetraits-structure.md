---
title: Srwlockexclusivetraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49f1f50b3fa9e34da8831c1cec138b6aefec27a5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649270"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits – struktura
Popisuje běžné vlastnosti `SRWLock` třídy ve výhradním režimu zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct SRWLockExclusiveTraits;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`Type`|Synonymum pro ukazatel [SRWLOCK](../windows/srwlock-class.md) třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SRWLockExclusiveTraits::GetInvalidValue – metoda](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|Načte **srwlockexclusivetraits –** objekt, který je pořád platný.|  
|[SRWLockExclusiveTraits::Unlock – metoda](../windows/srwlockexclusivetraits-unlock-method.md)|Uvolní výhradní kontrolu zadaného `SRWLock` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SRWLockExclusiveTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::HandleTraits – obor názvů](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)