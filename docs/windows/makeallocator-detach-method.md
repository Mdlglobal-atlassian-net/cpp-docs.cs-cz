---
title: Makeallocator::detach – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50afca04492c29aa526f7a004c6e0f725022e9ba
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="makeallocatordetach-method"></a>MakeAllocator::Detach – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline void Detach();  
```  
  
## <a name="remarks"></a>Poznámky  
 Zrušíte paměti přidělené [přidělte](../windows/makeallocator-allocate-method.md) z aktuálního objektu MakeAllocator metodu.  
  
 Když zavoláte Detach(), jste zodpovědní za odstraňování poskytované metodu přidělte paměť.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [MakeAllocator – třída](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)