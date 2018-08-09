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
ms.openlocfilehash: 5c7e2161c5451fe82e12918f00e8cb2cde37d336
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642312"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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