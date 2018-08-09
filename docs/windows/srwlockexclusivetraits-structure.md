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
ms.openlocfilehash: d6543ada6840b292d6a7b981eefeab41642c42df
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017929"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits – struktura
Popisuje běžné vlastnosti `SRWLock` třídy ve výhradním režimu zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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