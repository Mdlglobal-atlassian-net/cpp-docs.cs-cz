---
title: "Mutextraits – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs: C++
helpviewer_keywords: MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd8dac513b5eec049fbb739ab79628d9f41c96b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mutextraits-structure"></a>MutexTraits – struktura
Definuje běžné vlastnosti [Mutex](../windows/mutex-class1.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct MutexTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[MutexTraits::Unlock – metoda](../windows/mutextraits-unlock-method.md)|Uvolní výhradní kontrolu nad sdíleného prostředku.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::HandleTraits – obor názvů](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)