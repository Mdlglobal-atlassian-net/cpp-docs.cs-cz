---
title: AsyncStatusInternal – výčet | Microsoft Docs
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
ms.openlocfilehash: 150169442aa68395b4dc8a4f4c74951e877f18f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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