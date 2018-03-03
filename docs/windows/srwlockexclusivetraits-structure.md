---
title: "Srwlockexclusivetraits – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05e7b2a6814cefffee258909f4bab11fcfe34f1c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits – struktura
Popisuje běžné vlastnosti třída SRWLock ve výhradním režimu zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct SRWLockExclusiveTraits;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`Type`|Synonymum pro ukazatel [SRWLOCK](../windows/srwlock-class.md) třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SRWLockExclusiveTraits::GetInvalidValue – metoda](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|Načte srwlockexclusivetraits – objekt, který je vždy neplatný.|  
|[SRWLockExclusiveTraits::Unlock – metoda](../windows/srwlockexclusivetraits-unlock-method.md)|Uvolní výhradní kontrolu nad zadaný objekt SRWLock.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `SRWLockExclusiveTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::HandleTraits – obor názvů](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)