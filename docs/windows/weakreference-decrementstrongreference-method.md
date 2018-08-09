---
title: Weakreference::decrementstrongreference – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19dcb3e90faef86fd291381a7082e8b5bfa89069
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013454"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>Poznámky  
 Sníží počet silné referenční aktuálního **WeakReference** objektu.  
  
 Když počet odkazů silné klesne na nulu, silného odkazu se nastaví na **nullptr**.  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet odkazů sníží silné.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Weakreference – třída](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)