---
title: "Weakreference::incrementstrongreference – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
dev_langs: C++
helpviewer_keywords: IncrementStrongReference method
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 84923f3e25f5d294e6d052bf81f456d2353c624b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="weakreferenceincrementstrongreference-method"></a>WeakReference::IncrementStrongReference – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ULONG IncrementStrongReference();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet zvýšena silné odkazů.  
  
## <a name="remarks"></a>Poznámky  
 Zvětší počet silné odkaz na aktuální WeakReference objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
[WeakReference – třída](../windows/weakreference-class1.md)  
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)