---
title: Weakreference::weakreference – konstruktor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference, constructor
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e60b23a0c63ce1415765dd1f94863540849f975
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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