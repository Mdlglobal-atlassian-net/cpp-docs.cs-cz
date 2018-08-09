---
title: Asyncstatusinternal – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs:
- C++
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eeaef23178829163725b78685b3460913f53f2c2
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652796"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal – výčet
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Poznámky  
 Určuje mapování mezi interní výčty pro stav asynchronní operace a `Windows::Foundation::AsyncStatus` výčtu.  
  
## <a name="members"></a>Členové  
 `_Created`  
 Ekvivalent `::Windows::Foundation::AsyncStatus::Created`  
  
 `_Started`  
 Ekvivalent `::Windows::Foundation::AsyncStatus::Started`  
  
 `_Completed`  
 Ekvivalent `::Windows::Foundation::AsyncStatus::Completed`  
  
 `_Cancelled`  
 Ekvivalent `::Windows::Foundation::AsyncStatus::Cancelled`  
  
 `_Error`  
 Ekvivalent `::Windows::Foundation::AsyncStatus::Error`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)