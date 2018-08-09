---
title: Weakreference::incrementstrongreference – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- IncrementStrongReference method
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 764a47fe03a2ad9f4e4d3d64a5627acc9c72d1b5
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018868"
---
# <a name="weakreferenceincrementstrongreference-method"></a>WeakReference::IncrementStrongReference – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
ULONG IncrementStrongReference();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet zvýšena silného odkazu.  
  
## <a name="remarks"></a>Poznámky  
 Zvýší počet odkazů silné aktuálního **WeakReference** objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Weakreference – třída](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)