---
title: Namespace Microsoft::WRL::Wrappers::HandleTraits | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs:
- C++
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aec9ff1b4294257f692d76a96960820379116b0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits – obor názvů
Popisuje vlastnosti běžné typy prostředků na základě popisovač.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="structures"></a>Struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[CriticalSectionTraits – struktura](../windows/criticalsectiontraits-structure.md)|Se specializuje `CriticalSection` objekt pro podporu neplatný kritická sekce nebo funkce, která se verze kritická sekce.|  
|[EventTraits – struktura](../windows/eventtraits-structure.md)|Definuje vlastnosti `Event` třída popisovač.|  
|[FileHandleTraits – struktura](../windows/filehandletraits-structure.md)|Definuje vlastnosti popisovač souboru.|  
|[HANDLENullTraits – struktura](../windows/handlenulltraits-structure.md)|Definuje běžné vlastnosti neinicializovaný popisovač.|  
|[HANDLETraits – struktura](../windows/handletraits-structure.md)|Definuje běžné vlastnosti popisovač.|  
|[MutexTraits – struktura](../windows/mutextraits-structure.md)|Definuje běžné vlastnosti [Mutex](../windows/mutex-class1.md) třídy.|  
|[SemaphoreTraits – struktura](../windows/semaphoretraits-structure.md)|Definuje běžné vlastnosti semaforu pro objekt.|  
|[SRWLockExclusiveTraits – struktura](../windows/srwlockexclusivetraits-structure.md)|Popisuje běžné vlastnosti `SRWLock` třídy ve výhradním režimu zámku.|  
|[SRWLockSharedTraits – struktura](../windows/srwlocksharedtraits-structure.md)|Popisuje běžné vlastnosti `SRWLock` třídy ve sdíleném režimu zámku.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)