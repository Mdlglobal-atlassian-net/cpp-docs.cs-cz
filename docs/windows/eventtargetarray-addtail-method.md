---
title: Eventtargetarray::addtail – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
dev_langs:
- C++
helpviewer_keywords:
- AddTail method
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e80bf6d4313be5c90b4b4486cb31f3705252f33
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651262"
---
# <a name="eventtargetarrayaddtail-method"></a>EventTargetArray::AddTail – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void AddTail(  
   _In_ IUnknown* element  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *– Element*  
 Ukazatel na obslužnou rutinu události pro připojení.  
  
## <a name="remarks"></a>Poznámky  
 Obslužné rutiny zadané události připojí na konec vnitřní pole obslužných rutin událostí.  
  
 **AddTail()** je určena pro použití interně pomocí pouze `EventSource` třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Eventtargetarray – třída](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)