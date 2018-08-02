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
ms.openlocfilehash: a68189c461453dc72585ff4034df5ba69bb41bd5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464873"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal – výčet
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Poznámky  
 Určuje mapování mezi interní výčty pro stav asynchronní operace a `Windows::Foundation::AsyncStatus` výčtu.  
  
## <a name="members"></a>Členové  
 *_Created*  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: vytvořili  
  
 *_Started*  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: spuštění  
  
 *_Completed*  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: dokončeno  
  
 *_Cancelled*  
 Ekvivalentní:: Windows::Foundation::AsyncStatus:: zrušeno  
  
 *_Podrobnosti*  
 Ekvivalentní:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)