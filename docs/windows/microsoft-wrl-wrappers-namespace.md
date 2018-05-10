---
title: 'Microsoft::WRL:: wrappers – Namespace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa666c1a5de2962a4479b355966c1e8282f2989b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers – obor názvů
Definuje obálku typy prostředků pořízení je inicializace (RAII), které zjednodušit správu doba platnosti objektů, řetězce a obslužné rutiny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace Microsoft::WRL::Wrappers;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="typedefs"></a>Typedefs  
  
|Název|Popis|  
|----------|-----------------|  
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[CriticalSection – třída](../windows/criticalsection-class.md)|Představuje objekt kritická sekce.|  
|[Event – třída (knihovna šablon C++ prostředí Windows Runtime)](../windows/event-class-windows-runtime-cpp-template-library.md)|Představuje událost.|  
|[HandleT – třída](../windows/handlet-class.md)|Představuje popisovač objektu.|  
|[HString – třída](../windows/hstring-class.md)|Poskytuje podporu pro manipulaci s HSTRING obslužné rutiny.|  
|[HStringReference – třída](../windows/hstringreference-class.md)|Představuje HSTRING, který je vytvořený z existujícího řetězce.|  
|[Mutex – třída](../windows/mutex-class1.md)|Představuje objekt synchronizace, kterými se řídí výhradně sdíleného prostředku.|  
|[RoInitializeWrapper – třída](../windows/roinitializewrapper-class.md)|Inicializuje prostředí Windows Runtime.|  
|[Semaphore – třída](../windows/semaphore-class.md)|Představuje objekt synchronizace, který řídí sdílený prostředek, který podporuje omezený počet uživatelů.|  
|[SRWLock – třída](../windows/srwlock-class.md)|Představuje zámek pro tenký čtečky nebo zápis.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)