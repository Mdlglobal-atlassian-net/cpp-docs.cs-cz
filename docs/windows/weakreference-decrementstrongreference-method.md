---
title: "Weakreference::decrementstrongreference – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs: C++
helpviewer_keywords: DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bda6de03ce17db7ebac751865686c3e74a26d0d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>Poznámky  
 Snižuje počet silné odkaz na aktuální objekt WeakReference.  
  
 Pokud počet silné odkazů klesne na nulu, odkaz na silné je nastavena na `nullptr`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet odečte silné odkazů.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
[WeakReference – třída](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)