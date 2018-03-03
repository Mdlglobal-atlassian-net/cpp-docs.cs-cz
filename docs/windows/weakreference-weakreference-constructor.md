---
title: "Weakreference::weakreference – konstruktor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference, constructor
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8608c787b0b5b07c4e619443e751d21d14b0a811
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="weakreferenceweakreference-constructor"></a>WeakReference::WeakReference – konstruktor
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WeakReference();  
```  
  
## <a name="remarks"></a>Poznámky  
 Inicializuje novou instanci třídy [WeakReference – třída](../windows/weakreference-class1.md).  
  
 Je inicializováno ukazatele silné odkaz pro objekt WeakReference `nullptr`, a počet silné odkaz je inicializováno 1.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
    
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)