---
title: Invokehelper::callback_ – datový člen | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::callback_
dev_langs:
- C++
helpviewer_keywords:
- callback_ data member
ms.assetid: 6f0cbf6d-0448-46f8-ba71-bd6fd8702e3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0d6d767a77b68ad8585da711861d942abbe6b686
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013490"
---
# <a name="invokehelpercallback-data-member"></a>InvokeHelper::callback_ – datový člen
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
TCallback callback_;  
```  
  
## <a name="remarks"></a>Poznámky  
 Reprezentuje obslužnou rutinu události pro volání při výskytu události.  
  
 `TCallback` Parametr šablony určuje typ obslužné rutiny události.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Invokehelper – struktura](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)