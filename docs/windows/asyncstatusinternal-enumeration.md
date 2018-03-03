---
title: "AsyncStatusInternal – výčet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs:
- C++
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd277fecb0bc63d5ee823af98df8aa298b285964
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal – výčet
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Poznámky  
 Určuje mapování mezi interní výčty pro stav asynchronní operace a **Windows::Foundation::AsyncStatus** výčtu.  
  
## <a name="members"></a>Členové  
 `_Created`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: vytvořen  
  
 `_Started`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: spustila  
  
 `_Completed`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: dokončena  
  
 `_Cancelled`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: zrušena  
  
 `_Error`  
 Ekvivalentní:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)