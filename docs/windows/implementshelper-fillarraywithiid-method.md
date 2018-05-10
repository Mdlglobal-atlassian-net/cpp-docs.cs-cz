---
title: Implementshelper::fillarraywithiid – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: f60035ee-b7d6-4a08-966d-f88c646944c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9313ade1f5731319732a2ee3efc0af191af14f05
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="implementshelperfillarraywithiid-method"></a>ImplementsHelper::FillArrayWithIid – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void FillArrayWithIid(  
   _Inout_ unsigned long *index,   
   _Inout_ IID* iids) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 Index počítaný od nuly určující počáteční elementu pole pro tuto operaci. Po dokončení této operace `index` se zvýší o 1.  
  
 `iids`  
 Pole typu identifikátory IID.  
  
## <a name="remarks"></a>Poznámky  
 Vloží zadané parametrem aktuální šablony zeroth do elementu zadané pole ID rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Implementshelper – struktura](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)