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
ms.openlocfilehash: c606a1a7d32a02442e767a31543a76a4dccf295e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652471"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits – struktura
Popisuje běžné vlastnosti `SRWLock` třídy ve sdíleném režimu zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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